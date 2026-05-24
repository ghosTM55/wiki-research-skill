# Wiki Research Skill

[中文](README.md) | [English](README.en.md)

A lightweight wiki-source enhancement skill for normal AI-agent search and research. Once installed, the agent should automatically consider Wikipedia, Wikidata, official/project wikis, Fandom/community wikis, MediaWiki sites, and similar sources when relevant, and skip them when they are not useful.

> **Zero dependencies, strategy-only.** This skill does not bundle search tools, depend on a specific search engine, or require any MCP server or external API. It works with whatever search, browser, web extraction, or MCP tools the agent already has.

## Features

- Separates the roles of Wikipedia, Wikidata, official wikis, project wikis, Fandom/community wikis, and current sources.
- Useful for entertainment/IP/lore research, project knowledge, entity relationships, timelines, and cross-language narrative differences.
- Designed to fit into existing deep research, market research, competitive intelligence, or KBS/Obsidian workflows without requiring users to write complex prompts.
- No specific search engine, MCP server, or external dependency required; usable in Hermes, Codex, Claude Code, and other agents that support `SKILL.md`.

## Quick use

After installation, users should not need to say “use wiki-research” in every prompt. They can ask normal research questions, for example:

```text
Research the background, worldbuilding, main factions, and character relationships in Cyberpunk 2077.
```

```text
Look up the background, maintainers, and related projects for this open-source project.
```

The agent should decide automatically whether `wiki-research` is useful:

- While deciding, recognize high-confidence triggers such as worldbuilding, factions, character relationships, IP settings, official wiki, Fandom, Wikidata, community-maintained sources, 世界观、势力、角色关系、作品设定、IP设定、社区整理.
- If relevant, use the agent’s existing search/browser/MCP tools to include Wikipedia, Wikidata, official/project wikis, Fandom/community wikis, and similar sources in the search.
- When useful, extract aliases, entity relationships, work/character/organization links, lore/canon, timelines, or community taxonomies.
- In the answer, briefly label whether information comes from official, encyclopedia, community-maintained, or still-to-be-verified sources.
- If not relevant, skip the skill and continue with the main research workflow.

## When to use

- Background research on concepts, people, organizations, places, events, works, or franchises.
- Entertainment/IP research: lore, canon, character relationships, worldbuilding, factions, items, skills, storylines, episodes, chapters, and quests.
- Finding official wikis, project wikis, Fandom, wiki.gg, Miraheze, MediaWiki sites, or other community-maintained knowledge bases.
- Mapping entity relationships, aliases, multilingual names, timelines, and knowledge graph candidates.
- Comparing narrative differences across language editions or community wikis.
- Adding terminology, entities, related pages, and reliability boundaries inside ordinary search or deep research.

## When not to use as the main source

Do not rely on wiki sources as the main evidence for:

- breaking news, funding, market size, pricing, policy, regulation, product status, or current API behavior;
- legal, compliance, financial, or commercial conclusions;
- questions that require official documentation, papers, filings, market reports, live data, or primary sources;
- broad research tasks already handled by a dedicated deep research skill.

For those tasks, wiki sources are useful for background, terminology, and disambiguation only.

## Working with existing research skills

`wiki-research` is not a full research workflow that users need to start manually, and it is not a search executor. It is an automatic source-selection rule: when the research target benefits from wiki-style sources, the agent uses it to decide which wiki-style sources are worth adding; actual searching is handled by the agent’s existing search, browser, web extraction, or MCP tools.

Recommended behavior:

```text
The main research/search workflow still owns decomposition, search, evidence judgment, synthesis, and final output.
wiki-research only decides and adds wiki-style sources, aliases, entity relationships, lore/canon, timelines, and reliability notes when relevant.
```

## Source layers

| Source type | Primary use | Cautions |
|---|---|---|
| Wikipedia | General background, stable facts, notable people/companies/works/events | Insufficient for market, legal, product, pricing, or current-state claims |
| Wikidata | Structured entity relationships, aliases, multilingual names, dates, work-person-organization links | Best for graph/disambiguation; explanations still need article/wiki/primary-source context |
| Official/project wiki | Software, games, protocols, platforms, project knowledge, official mechanics/canon | Check version, maintenance status, and update date |
| Fandom/community wiki | Entertainment/IP lore, characters, worldbuilding, fan taxonomy, long-tail details | Distinguish official canon, community consensus, speculation, and outdated pages |
| Current web/news/reports | Recent changes, business status, market data, policy, pricing, product updates | Usually belongs to the broader research workflow, not this skill |

## Installation and configuration

### Recommended: install once, let the agent auto-match

Install `SKILL.md` into the agent’s global or project-level skills directory. For agents that support automatic skill matching, users can ask normal research questions; they do not need to mention `wiki-research` in every prompt.

Project-level installation is best for a specific team or research project. Global installation is useful for users who often research IP, lore, entity relationships, project background, or community-maintained knowledge.

### Hermes Agent

If your Hermes version supports installing skills from a GitHub URL:

```bash
hermes skills install https://github.com/ghosTM55/wiki-research-skill
```

If your Hermes version needs a direct `SKILL.md` URL:

```bash
hermes skills install https://raw.githubusercontent.com/ghosTM55/wiki-research-skill/main/SKILL.md --name wiki-research
```

Start a new session after installation. You usually do not need to run `/skill wiki-research`; use it only for debugging, demos, or when you explicitly want to force-load the skill:

```text
/skill wiki-research
```

### Codex / Claude Code / other Agent Skills-compatible tools

Install `SKILL.md` into the relevant global or project-level skills directory. Different agents trigger skills differently: some auto-match from the skill description; others may need a project rule such as “during search/research tasks, wiki-research may be used automatically to add wiki-style sources.”

Common project-level layout:

```text
.agents/skills/wiki-research/SKILL.md
```

### Manual install

```bash
mkdir -p ~/.hermes/skills/research/wiki-research
curl -L https://raw.githubusercontent.com/ghosTM55/wiki-research-skill/main/SKILL.md \
  -o ~/.hermes/skills/research/wiki-research/SKILL.md
```

## Usage examples

### Normal user requests

```text
Research this IP’s worldbuilding, character relationships, and common community classifications.
```

```text
Look up this project’s background, core concepts, related organizations, and history.
```

### What the agent should add automatically

```text
If relevant, search Wikipedia, Wikidata, official/project wikis, and Fandom/community wikis.
Extract useful aliases, entity relationships, lore/canon, timelines, community categories, and reliability notes.
If not relevant, skip wiki sources.
```

## Related skill: ghost-research

[`ghost-research`](https://github.com/ghosTM55/ghost-research-skill) is a horizontal-vertical deep research skill for structured KBS/Obsidian research reports. It pairs with `wiki-research` as follows:

- `wiki-research`: lightweight and automatic; adds wiki-style sources and relationship information during normal search/research when relevant.
- `ghost-research`: heavier and end-to-end; produces structured deep research using longitudinal history, cross-sectional comparison, synthesis, evidence evaluation, and Markdown output.

Recommended pairing: when a user asks for deep research, `ghost-research` can own the main workflow. If the target involves encyclopedia background, entity relationships, IP/lore/canon, project wikis, or community knowledge, `wiki-research` can quietly add relevant sources and relationship clues in the background.

## Repository structure

```text
wiki-research-skill/
├── SKILL.md
├── README.md
├── README.en.md
├── LICENSE
└── .gitignore
```

## License

MIT
