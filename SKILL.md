---
name: wiki-research
description: Use when researching topics where wiki-style sources may provide useful background, entity relationships, lore, canon, project knowledge, or community-maintained structure. Routes between Wikipedia, Wikidata, official/project wikis, Fandom/community wikis, and current web sources.
version: 1.0.0
author: Thomas Yao / ghosTM55
license: MIT
metadata:
  hermes:
    tags: [research, wiki, wikipedia, wikidata, fandom, mediawiki, lore, knowledge-graph]
    related_skills: [deep-research, web-research, obsidian, llm-wiki]
---

# Wiki Research

Use this skill to decide when and how to use wiki-style sources during research. It is not a replacement for a deep research skill, a web search skill, or a private knowledge-base skill. It is a routing and source-evaluation layer for Wikipedia, Wikidata, official/project wikis, Fandom/community wikis, and other MediaWiki-like knowledge bases.

## Core Principle

Wiki-style sources are strongest when they provide one or more of these:

- stable background facts;
- entity disambiguation;
- relationships between people, works, organizations, places, concepts, and dates;
- canon/lore structures for entertainment and fictional worlds;
- project or product knowledge maintained by an official or expert community;
- a map of related concepts that helps plan further research.

Do not treat any wiki as automatically authoritative. Route by source type, then cross-check important claims against better sources when the answer affects strategy, factual accuracy, commercial judgment, legal/regulatory claims, or public-facing work.

## When to Use

Use `wiki-research` when the user asks about:

- background or history of a concept, person, organization, work, franchise, technology, project, place, or event;
- entertainment/IP research: lore, canon, characters, worldbuilding, episodes, quests, factions, timelines, relationships, fan terminology;
- whether a topic has a dedicated wiki, official knowledge base, fan wiki, project wiki, or structured public knowledge graph;
- entity relationships, timelines, knowledge graphs, taxonomies, or cross-language/wiki narrative differences;
- research planning where wiki pages can reveal related concepts, names, alternate titles, aliases, and source trails.

Do not use this skill as the primary workflow for:

- current news, market prices, funding, policy changes, product availability, API behavior, or legal/regulatory updates;
- tasks where official documentation, primary sources, filings, papers, or current market reports are clearly required;
- broad deep research when the user already has a dedicated deep research skill activated. In that case, use this skill only as a source-routing subroutine.

## Source Types and Their Roles

| Source type | Best for | Cautions |
|---|---|---|
| Wikipedia | General background, stable public facts, notable people/companies/works/events, starting bibliographies | Often incomplete for niche/fast-moving topics; not enough for market, legal, product, or current claims |
| Wikidata | Structured entity relationships, IDs, aliases, multilingual names, dates, parent/child relations, works/creators/organizations | A graph of claims, not a narrative explanation; still check references and qualifiers |
| Official/project wiki | Authoritative product, game, software, protocol, or community-maintained domain knowledge | Version drift; may mix docs, marketing, and community-maintained pages |
| Fandom/community wiki | Lore, canon debates, characters, long-tail entertainment details, fan taxonomy, episode/chapter/quest-level knowledge | Distinguish official canon, community consensus, speculation, fan interpretation, and outdated pages |
| Current web/news/reports | Recent events, business status, market data, product changes, policy and pricing | Use outside wiki-research; cite dates and sources |

## Relationship to Existing Research Skills

If the user already has a deep research, market research, competitive intelligence, academic research, or KBS-ingest skill, do not compete with it.

Use this skill as a **narrow source-routing layer**:

1. Identify whether wiki-style sources are useful for the topic.
2. Choose which wiki layer to consult first: Wikipedia, Wikidata, official/project wiki, Fandom/community wiki, or none.
3. Extract names, entities, aliases, timelines, lore structures, and related pages that improve the main research workflow.
4. Hand findings back to the active research skill as a background/fact/lore/entity map input.
5. Let the main research skill handle breadth, synthesis, judgment, report structure, and KBS persistence.

Recommended coordination language:

> Use `wiki-research` only to establish the wiki-source baseline: relevant wiki sources, entity/lore/canon structure, relationship graph candidates, and reliability notes. Then continue with the existing deep research workflow for current sources, analysis, and conclusions.

Avoid:

- running a full deep-research loop inside this skill;
- saving to a knowledge base unless the active KBS/Obsidian/LLM-wiki skill asks for it;
- treating community wiki content as verified fact without labeling its status.

## Workflow

### 1. Classify the task

Decide whether the topic is primarily:

- encyclopedia/background;
- entity/relationship graph;
- official project/product knowledge;
- entertainment lore/canon/community knowledge;
- cross-language or cross-community narrative comparison;
- current commercial/news/policy research.

If the task is mostly current commercial/news/policy research, use wiki sources only for background or entity disambiguation.

### 2. Pick the right wiki layer

Use this order as a default, adjusting for the domain:

- General public fact: Wikipedia first, then current/primary sources.
- Structured relationship: Wikidata first, then Wikipedia or domain wiki for explanation.
- Software/project/product: official docs or project wiki first, Wikipedia only for background.
- Entertainment/IP/lore: official wiki or canonical source first if available; then Fandom/community wiki for long-tail detail; Wikipedia for external public context.
- Niche community/domain: search for dedicated wikis, MediaWiki sites, wiki.gg, Miraheze, Fandom, project docs, and subreddit/community-maintained knowledge bases.

### 3. Gather useful wiki evidence

For each useful source, capture:

- source name and URL;
- source type: Wikipedia / Wikidata / official wiki / Fandom / community wiki / project wiki;
- last updated date if visible;
- key entities and aliases;
- relevant sections/pages;
- relationship candidates;
- reliability notes: official, community-maintained, unsourced, outdated, disputed, speculative, or cross-language difference.

### 4. Cross-check by claim type

Use a stricter source when claims matter:

- market, revenue, users, pricing, funding, release status → current official sources, filings, reports, or news;
- laws, platform policy, compliance → official legal/policy sources;
- product/API behavior → official docs and live tests;
- canon/lore → official source if possible; otherwise label community wiki as community-maintained;
- foundational background → Wikipedia/Wikidata acceptable as a starting point, but cite source and date for important use.

### 5. Output in layers

Prefer this structure:

```markdown
## Wiki-source baseline
- Source map: which wiki sources were useful and why
- Key entities / aliases
- Timeline or relationship candidates
- Lore/canon/project-knowledge structure, if relevant

## Reliability notes
- Official vs community-maintained
- Unsourced/speculative/outdated/disputed areas
- Cross-language or cross-wiki differences

## What still needs current or primary-source research
- Market/current/product/legal claims that should not rely on wiki sources
```

If another research skill is active, keep this output compact so it can be used as input to that workflow.

## Wikidata Mental Model

Wikidata is closer to a public structured knowledge graph than to a normal article wiki. Think of it as:

```text
entity -> property -> value
The Matrix -> director -> The Wachowskis
The Matrix -> publication date -> 1999
The Matrix -> genre -> science fiction film
```

Compared with an Obsidian graph:

- Obsidian links are personal/freeform and often imply relationships through context.
- Wikidata links are public, typed relationships with properties, qualifiers, aliases, and references.

Use Wikidata for structure and disambiguation. Use article/wiki sources for explanation and narrative.

## Common Pitfalls

1. **Overusing wiki sources for current facts.** Wikipedia and Fandom are often too slow or incomplete for current business, product, policy, or market claims.
2. **Treating Fandom as official canon.** Community wiki pages are useful but must be labeled as community-maintained unless backed by official/canonical sources.
3. **Ignoring official wikis.** For games, software, protocols, and creator platforms, official docs or official wikis usually outrank Wikipedia.
4. **Forgetting Wikidata qualifiers.** Wikidata claims can have dates, scope, ranks, and references. Avoid flattening nuanced claims into timeless facts.
5. **Competing with a deep research skill.** This skill should provide source routing and a wiki baseline, not duplicate the main research workflow.
6. **Missing cross-language differences.** For culturally sensitive or region-specific topics, compare language editions or community wikis when narrative framing matters.

## Verification Checklist

Before finalizing wiki-based research, verify:

- [ ] The output labels source types clearly.
- [ ] Community/Fandom claims are not presented as official fact unless verified.
- [ ] Current or commercial claims are backed by current non-wiki sources.
- [ ] Wikidata-derived relationships are treated as structured claims, not full explanations.
- [ ] Any active deep research/KBS skill remains the owner of final synthesis and persistence.
