---
name: wiki-research
description: Use automatically during search or research when wiki-style sources may help with background, entities, aliases, relationships, timelines, lore/canon, project knowledge, or community-maintained structure. Add relevant Wikipedia, Wikidata, official/project wiki, Fandom/community wiki, or MediaWiki-style sources without requiring the user to ask for this skill explicitly.
version: 1.0.0
author: Thomas Yao / ghosTM55
license: MIT
metadata:
  hermes:
    tags: [research, wiki, wikipedia, wikidata, fandom, mediawiki, lore, knowledge-graph]
    related_skills: [deep-research, web-research, ghost-research, obsidian, llm-wiki]
---

# Wiki Research

Use this skill as an automatic enhancement to normal search and research. The user should not need to ask for `wiki-research` explicitly. When a task may benefit from wiki-style sources, add the right Wikipedia, Wikidata, official/project wiki, Fandom/community wiki, or MediaWiki-like sources; when wiki sources are not useful, skip them.

## Core Principle

Wiki-style sources are strongest when they provide one or more of these:

- stable background facts;
- entity disambiguation;
- relationships between people, works, organizations, places, concepts, and dates;
- canon/lore structures for entertainment and fictional worlds;
- project or product knowledge maintained by an official or expert community;
- related concepts that make the answer more useful.

Do not treat any wiki as automatically authoritative. Use wiki sources as background, relationship, or community-structure inputs; cross-check important claims against official/current/primary sources when the answer affects strategy, factual accuracy, commercial judgment, legal/regulatory claims, or public-facing work.

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
- broad deep research when the user already has a dedicated deep research skill activated. In that case, use this skill only as a quiet background helper.

## Source Types and Their Roles

| Source type | Best for | Cautions |
|---|---|---|
| Wikipedia | General background, stable public facts, notable people/companies/works/events, starting bibliographies | Often incomplete for niche/fast-moving topics; not enough for market, legal, product, or current claims |
| Wikidata | Structured entity relationships, IDs, aliases, multilingual names, dates, parent/child relations, works/creators/organizations | A graph of claims, not a narrative explanation; still check references and qualifiers |
| Official/project wiki | Authoritative product, game, software, protocol, or community-maintained domain knowledge | Version drift; may mix docs, marketing, and community-maintained pages |
| Fandom/community wiki | Lore, canon debates, characters, long-tail entertainment details, fan taxonomy, episode/chapter/quest-level knowledge | Distinguish official canon, community consensus, speculation, fan interpretation, and outdated pages |
| Current web/news/reports | Recent events, business status, market data, product changes, policy and pricing | Use outside wiki-research; cite dates and sources |

## Relationship to Existing Research Skills

If another deep research, market research, competitive intelligence, academic research, KBS-ingest skill, or `ghost-research` is active, do not compete with it and do not require a separate user prompt. Use this skill silently as a small subroutine when useful.

Expected behavior:

1. Notice when the search/research target may have useful wiki-style sources.
2. Add those sources to the search only when they are relevant.
3. Extract names, aliases, entities, timelines, relationships, lore/canon distinctions, related pages, or community categories that improve the answer.
4. Briefly label source type and reliability when it matters.
5. Let the main research workflow, such as `ghost-research`, handle broad search, synthesis, judgment, report structure, and persistence.

Avoid:

- asking the user to write a special prompt just to trigger this skill;
- turning the task into a separate wiki-only report unless the user asks for one;
- running a full deep-research loop inside this skill;
- saving to a knowledge base unless the active KBS/Obsidian/LLM-wiki skill asks for it;
- treating community wiki content as verified fact without labeling its status.

## Workflow

### 1. Decide whether wiki sources are useful

During normal search/research, quickly decide whether the target involves:

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

### 5. Output only what helps

Do not force a special report format. In a normal answer, include a short wiki-related note only when it adds value:

```markdown
Wiki-related sources checked: [Wikipedia / Wikidata / official wiki / Fandom / community wiki, if useful]
Useful additions: [aliases, entity relationships, lore/canon, timeline, related pages, community categories]
Reliability: [official vs encyclopedia vs community-maintained vs needs verification]
```

If wiki sources were not useful, do not mention this skill.

## Using Wikidata

Use Wikidata when the task benefits from structured public data rather than narrative explanation:

- entity disambiguation and canonical IDs;
- aliases and multilingual names;
- typed relationships such as creator, director, publisher, parent organization, part of series, location, and date;
- timeline or relationship-graph candidates.

Treat Wikidata results as structured claims. Check qualifiers, dates, ranks, and references when the claim matters. Use article/wiki sources for explanation, narrative context, and domain nuance.

## Common Pitfalls

1. **Overusing wiki sources for current facts.** Wikipedia and Fandom are often too slow or incomplete for current business, product, policy, or market claims.
2. **Treating Fandom as official canon.** Community wiki pages are useful but must be labeled as community-maintained unless backed by official/canonical sources.
3. **Ignoring official wikis.** For games, software, protocols, and creator platforms, official docs or official wikis usually outrank Wikipedia.
4. **Forgetting Wikidata qualifiers.** Wikidata claims can have dates, scope, ranks, and references. Avoid flattening nuanced claims into timeless facts.
5. **Competing with a deep research skill.** This skill should quietly enhance search with wiki-style sources, not duplicate the main research workflow.
6. **Missing cross-language differences.** For culturally sensitive or region-specific topics, compare language editions or community wikis when narrative framing matters.

## Verification Checklist

Before finalizing wiki-based research, verify:

- [ ] The output labels source types clearly.
- [ ] Community/Fandom claims are not presented as official fact unless verified.
- [ ] Current or commercial claims are backed by current non-wiki sources.
- [ ] Wikidata-derived relationships are treated as structured claims, not full explanations.
- [ ] Any active deep research/KBS skill remains the owner of final synthesis and persistence.
