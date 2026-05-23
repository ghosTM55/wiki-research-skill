# Wiki Research Skill

[中文](README.md) | [English](README.en.md)

A wiki source-routing skill for AI agents. It helps an agent decide when to use Wikipedia, Wikidata, official/project wikis, Fandom/community wikis, MediaWiki sites, and when to switch to current web sources, official documentation, or a broader deep research workflow.

## Features

- Separates the roles of Wikipedia, Wikidata, official wikis, project wikis, Fandom/community wikis, and current sources.
- Useful for entertainment/IP/lore research, project knowledge, entity relationships, timelines, and cross-language narrative differences.
- Designed to work as a source-routing layer before existing deep research, market research, competitive intelligence, or KBS/Obsidian ingest skills.
- No MCP server or external dependency required; usable in Hermes, Codex, Claude Code, and other agents that support `SKILL.md`.

## Quick use

After installing or referencing this skill in your AI agent, prompt it like this:

```text
Use wiki-research to establish the wiki-source baseline for this topic: relevant Wikipedia/Wikidata pages, official/project wikis, Fandom/community wikis, entity aliases, lore/canon structure, relationship graph candidates, and reliability notes. Then continue with my existing deep research workflow for current sources and analysis.
```

## When to use

- Background research on concepts, people, organizations, places, events, works, or franchises.
- Entertainment/IP research: lore, canon, character relationships, worldbuilding, factions, items, skills, storylines, episodes, chapters, and quests.
- Finding official wikis, project wikis, Fandom, wiki.gg, Miraheze, MediaWiki sites, or other community-maintained knowledge bases.
- Mapping entity relationships, aliases, multilingual names, timelines, and knowledge graph candidates.
- Comparing narrative differences across language editions or community wikis.
- Establishing terminology, entities, source maps, and reliability boundaries before deep research.

## When not to use as the main source

Do not rely on wiki sources as the main evidence for:

- breaking news, funding, market size, pricing, policy, regulation, product status, or current API behavior;
- legal, compliance, financial, or commercial conclusions;
- questions that require official documentation, papers, filings, market reports, live data, or primary sources;
- broad research tasks already handled by a dedicated deep research skill.

For those tasks, wiki sources are useful for background, terminology, and disambiguation only.

## Working with existing research skills

`wiki-research` should not replace an existing research skill. It is a pre-research routing and source-layering skill.

```text
wiki-research owns:
- deciding whether wiki-style sources are useful
- choosing Wikipedia / Wikidata / official wiki / Fandom / community wiki
- extracting entities, aliases, lore/canon structure, and relationship candidates
- labeling source reliability and claims that need further verification

The main research skill owns:
- decomposition
- broad search
- evidence evaluation
- synthesis
- report structure
- KBS/Obsidian persistence
```

Recommended coordination pattern:

```text
First use wiki-research as a source-routing step. Keep the output compact and structured. Then pass the wiki-source baseline into the active deep research skill.
```

## Source layers

| Source type | Primary use | Cautions |
|---|---|---|
| Wikipedia | General background, stable facts, notable people/companies/works/events | Insufficient for market, legal, product, pricing, or current-state claims |
| Wikidata | Structured entity relationships, aliases, multilingual names, dates, work-person-organization links | Best for graph/disambiguation; explanations still need article/wiki/primary-source context |
| Official/project wiki | Software, games, protocols, platforms, project knowledge, official mechanics/canon | Check version, maintenance status, and update date |
| Fandom/community wiki | Entertainment/IP lore, characters, worldbuilding, fan taxonomy, long-tail details | Distinguish official canon, community consensus, speculation, and outdated pages |
| Current web/news/reports | Recent changes, business status, market data, policy, pricing, product updates | Usually belongs to the broader research workflow, not this skill |

## Installation

### Hermes Agent

If your Hermes version supports installing skills from a GitHub URL:

```bash
hermes skills install https://github.com/ghosTM55/wiki-research-skill
```

If your Hermes version needs a direct `SKILL.md` URL:

```bash
hermes skills install https://raw.githubusercontent.com/ghosTM55/wiki-research-skill/main/SKILL.md --name wiki-research
```

Start a new session and load the skill when needed:

```text
/skill wiki-research
```

### Codex / Claude Code / other Agent Skills-compatible tools

Install `SKILL.md` into the relevant global or project-level skills directory. Project-level installation is recommended to avoid over-triggering.

Common project-level layout:

```text
.agents/skills/wiki-research/SKILL.md
```

Use your agent’s documentation for the exact installation command and directory.

### Manual install

```bash
mkdir -p ~/.hermes/skills/research/wiki-research
curl -L https://raw.githubusercontent.com/ghosTM55/wiki-research-skill/main/SKILL.md \
  -o ~/.hermes/skills/research/wiki-research/SKILL.md
```

## Prompt examples

### Entertainment/IP/lore

```text
Use wiki-research to map the wiki-source baseline for this franchise: official wiki, Fandom/community wiki, Wikipedia/Wikidata, major lore pages, canon status, character/faction/timeline structure, and reliability caveats. Do not do full market research yet.
```

### With deep research

```text
Before running the deep research skill, use wiki-research as a narrow routing step: identify useful wiki-style sources, entity aliases, relationship graph candidates, and claims that must be verified with current/primary sources.
```

### Current-fact limits

```text
Use wiki-research only for stable background and entity/lore mapping. For current product status, pricing, policy, market size, revenue, or funding, explicitly switch to current web/official sources.
```

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
