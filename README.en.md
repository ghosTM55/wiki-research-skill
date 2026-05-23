# Wiki Research Skill

> 中文说明: [README.md](README.md)

`wiki-research` is a lightweight research-routing skill for AI agents. It is not a Wikipedia plugin, a deep research workflow, or a knowledge-base ingest tool. It helps an agent decide when and how to use wiki-style sources such as Wikipedia, Wikidata, official/project wikis, Fandom/community wikis, MediaWiki sites, wiki.gg, Miraheze, and domain-specific knowledge bases.

## What problem does it solve?

Many research tasks benefit from a “wiki baseline” before broader web research begins:

- What are the stable background facts about this concept, person, company, work, IP, or franchise?
- Is there an official wiki, project wiki, Fandom/community wiki, or dedicated knowledge base?
- Where are entertainment lore, canon, character relationships, timelines, and fan taxonomies best maintained?
- Can Wikidata provide entity relationships, aliases, multilingual names, dates, or graph candidates?
- Which claims are official, community-maintained, speculative, outdated, or disputed?
- Which claims require current web, official, market, legal, or primary-source verification?

The goal is not to send every research task to Wikipedia. The goal is better source routing.

## When to use it

Use this skill for:

- background research on concepts, people, organizations, places, events, works, or franchises;
- entertainment/IP research: lore, canon, characters, worlds, factions, items, skills, episodes, chapters, quests, and fan terminology;
- finding dedicated wikis, official knowledge bases, project wikis, Fandom, wiki.gg, Miraheze, or MediaWiki sites;
- Wikidata-style entity relationships, timelines, aliases, multilingual names, and knowledge graph candidates;
- comparing narrative differences across language editions or community wikis;
- establishing facts, entities, terminology, and source maps before deep research.

Do not use it as the main workflow for:

- breaking news, funding, market size, pricing, policy, regulation, product availability, or current API behavior;
- legal, compliance, financial, or commercial conclusions;
- questions that clearly require official documentation, papers, filings, market reports, or live/current sources;
- broad research tasks where an existing deep research skill is already in charge.

For those tasks, wiki sources are background or disambiguation aids, not final evidence.

## How it should work with existing research skills

If a user already has a deep research, market research, competitive intelligence, academic research, Obsidian, or KBS-ingest skill, `wiki-research` should not replace it.

Use `wiki-research` as a **narrow source-routing layer**:

```text
Main research skill owns: decomposition, broad search, evidence evaluation, synthesis, report structure, and KBS persistence.
wiki-research owns: choosing useful wiki layers, building a wiki-source baseline, extracting entity/lore/canon/relationship candidates, and labeling reliability.
```

Recommended instruction for agents:

```text
Use wiki-research only to establish the wiki-source baseline: relevant wiki sources, entity/lore/canon structure, relationship graph candidates, and reliability notes. Then continue with the existing deep research workflow for current sources, analysis, and conclusions.
```

Avoid:

```text
Use wiki-research to run the entire deep research task.
```

Prefer:

```text
First use wiki-research to identify relevant Wikipedia, Wikidata, official wiki, Fandom/community wiki, entity aliases, lore/canon structure, and reliability caveats. Then continue with my existing deep research skill.
```

## Wiki source layers

| Source type | Best for | Cautions |
|---|---|---|
| Wikipedia | General background, stable facts, notable people/companies/works/events | Not enough for market, legal, product, pricing, or current claims |
| Wikidata | Structured entity relationships, aliases, multilingual names, dates, work-person-organization links | A knowledge graph, not an explanatory article; check qualifiers and references |
| Official/project wiki | Software, games, protocols, platforms, project knowledge, official mechanics/canon | Watch version drift and update dates |
| Fandom/community wiki | Entertainment/IP lore, characters, worldbuilding, fan taxonomy, long-tail details | Distinguish official canon, community consensus, speculation, and outdated pages |
| Current web/news/reports | Recent changes, business status, market data, policy, pricing, product updates | Often needed after wiki-research; not owned by this skill |

## Wikidata vs Obsidian graph

A useful mental model: Wikidata is like a public, structured, machine-readable knowledge graph. Obsidian is a personal freeform note graph.

```text
Obsidian:
[[The Matrix]] -> [[Wachowskis]] -> [[Cyberpunk]]
The relationship is usually implied by context.

Wikidata:
The Matrix -> director -> The Wachowskis
The Matrix -> genre -> science fiction film
The Matrix -> publication date -> 1999
The relationship is represented by explicit properties.
```

Therefore:

- Obsidian is good for personal knowledge organization and synthesis.
- Wikidata is good for public entity relationships, disambiguation, aliases, multilingual names, timelines, and batch queries.
- Wikipedia, Fandom, and official/project wikis are better for explanation, narrative, and contextual detail.

## Installation

### Hermes Agent

Copy the skill into your Hermes skills directory:

```bash
mkdir -p ~/.hermes/skills/research/wiki-research
cp SKILL.md ~/.hermes/skills/research/wiki-research/SKILL.md
```

Then load it in a new Hermes session:

```text
/skill wiki-research
```

Or ask explicitly:

```text
Use wiki-research to establish the wiki-source baseline for this topic.
```

### Codex / other Agent Skills-compatible tools

Place `SKILL.md` in the relevant agent skills directory, or at a project level such as:

```text
.agents/skills/wiki-research/SKILL.md
```

Different tools discover skills differently. Follow your agent’s documentation.

For Codex, prefer project-level use unless you frequently build wiki/lore/knowledge-graph research tools.

## Recommended prompts

### 1. Entertainment/IP/lore research

```text
Use wiki-research to map the wiki-source baseline for this franchise: official wiki, Fandom/community wiki, Wikipedia/Wikidata, major lore pages, canon status, character/faction/timeline structure, and reliability caveats. Do not do full market research yet.
```

### 2. Working with an existing deep research skill

```text
Before running the deep research skill, use wiki-research as a narrow routing step: identify useful wiki-style sources, entity aliases, relationship graph candidates, and claims that must be verified with current/primary sources.
```

### 3. Wikidata / knowledge graph

```text
Use wiki-research to decide whether Wikidata is useful for this topic. If useful, extract candidate entities, aliases, typed relationships, dates, and multilingual names. Explain which parts need article/wiki context rather than graph data.
```

### 4. Current-fact limits

```text
Use wiki-research only for stable background and entity/lore mapping. For current product status, pricing, policy, market size, revenue, or funding, explicitly switch to current web/official sources.
```

## Repository structure

```text
wiki-research-skill/
├── SKILL.md       # Main skill file
├── README.md      # Chinese README
├── README.en.md   # English README
├── LICENSE        # MIT
└── .gitignore
```

## License

MIT
