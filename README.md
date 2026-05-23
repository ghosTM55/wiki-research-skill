# Wiki Research Skill

> 默认中文说明。English version: [README.en.md](README.en.md)

`wiki-research` 是一个面向 AI agent 的轻量研究路由 Skill。它不是 Wikipedia 插件，也不是深度研究工具，而是帮助 agent 判断：什么时候应该把 Wikipedia、Wikidata、官方 Wiki、项目 Wiki、Fandom/社区 Wiki、MediaWiki 站点等 wiki-style sources 当作研究信息源，并如何与现有的深度研究、KBS、Obsidian 或 web research 流程协作。

## 它解决什么问题？

很多研究任务并不应该直接进入新闻/报告/搜索结果，而需要先建立一个“wiki 基线”：

- 这个概念/人物/公司/作品/IP 的基础事实是什么？
- 有没有专门的官方 Wiki、项目 Wiki、Fandom 或社区 Wiki？
- 娱乐内容里的角色、世界观、canon、lore、粉丝分类在哪里整理得最好？
- 这个主题的实体关系、别名、多语言名称、时间线能不能从 Wikidata 获得？
- 哪些信息只是社区共识或粉丝推测，不能当成官方事实？
- 哪些问题必须跳出 wiki，去查当前资料、官方文件、市场报告或新闻？

`wiki-research` 的目标是让 agent 在这些判断上更稳定，而不是把所有研究都导向 Wikipedia。

## 适用场景

适合用于：

- 概念、人物、组织、地点、事件、作品、franchise 的背景梳理；
- 娱乐/IP 研究：lore、canon、角色关系、剧情线、世界观、势力、物品、技能、episode/chapter/quest 级别细节；
- 查找某个领域是否有专门 wiki、官方知识库、项目 wiki、Fandom、wiki.gg、Miraheze、MediaWiki 站点；
- Wikidata 式实体关系、时间线、别名、多语言名称、知识图谱候选；
- 比较不同语言 Wikipedia、不同社区 Wiki 对同一主题的叙事差异；
- 在深度研究前，建立基础事实、实体、术语、来源地图。

不适合作为主流程用于：

- 最新新闻、融资、市场规模、价格、政策、法规、产品功能、API 当前行为；
- 法律/合规/财务/商业结论；
- 需要官方文档、论文、财报、行业报告或实时资料的问题；
- 已有深度研究 skill 正在主导的完整研究任务。

这些场景里，wiki 只能作为背景或实体消歧，不能作为最终依据。

## 与已有研究类 Skill 如何配合？

如果用户已经有深度研究、市场研究、竞争分析、学术研究、KBS/Obsidian ingest 等 skill，`wiki-research` 不应该替代它们。

正确用法是把 `wiki-research` 当作一个**窄的 source-routing layer**：

```text
主研究 skill 负责：问题拆解、广泛搜索、证据评估、综合判断、报告结构、KBS 写入
wiki-research 负责：判断该查哪类 wiki、建立 wiki-source baseline、整理实体/lore/canon/关系图谱候选、标注可靠性
```

推荐给 agent 的提示词：

```text
Use wiki-research only to establish the wiki-source baseline: relevant wiki sources, entity/lore/canon structure, relationship graph candidates, and reliability notes. Then continue with the existing deep research workflow for current sources, analysis, and conclusions.
```

中文提示：

```text
只用 wiki-research 建立 wiki 信息源基线：相关 wiki 来源、实体/lore/canon 结构、关系图谱候选和可靠性说明。之后继续使用已有深度研究流程处理当前资料、分析判断和结论。
```

避免这样使用：

```text
用 wiki-research 做完整深度研究。
```

更好的用法：

```text
先用 wiki-research 找出这个 IP/项目/概念相关的 Wikipedia、Wikidata、官方 Wiki、Fandom/社区 Wiki，并标注哪些是官方、哪些是社区维护、哪些需要当前资料验证；然后再进入我的 deep research skill。
```

## Wiki 来源分层

| 来源类型 | 适合 | 注意事项 |
|---|---|---|
| Wikipedia | 通用背景、稳定事实、人物/公司/作品/事件基础信息 | 不适合单独支持市场、法律、产品、当前新闻判断 |
| Wikidata | 结构化实体关系、别名、多语言名称、时间线、作品-人物-组织关系 | 是知识图谱，不是解释性文章；需要看 qualifier/reference |
| 官方/项目 Wiki | 软件、游戏、协议、平台、项目知识、官方机制/canon | 注意版本和更新日期 |
| Fandom/社区 Wiki | 娱乐/IP lore、角色、世界观、粉丝分类、长尾细节 | 必须区分官方 canon、社区整理、粉丝推测和过期内容 |
| 当前 web/news/reports | 最近变化、商业状态、市场数据、政策、价格、产品更新 | 不属于 wiki-research 的主要职责，但常常需要后续查询 |

## Wikidata 和 Obsidian 图谱的关系

你的直觉可以这样理解：Wikidata 有点像一个公共、结构化、机器可读的知识图谱；Obsidian 图谱是个人笔记之间的自由链接。

```text
Obsidian:
[[The Matrix]] -> [[Wachowskis]] -> [[Cyberpunk]]
关系通常靠上下文理解。

Wikidata:
The Matrix -> director -> The Wachowskis
The Matrix -> genre -> science fiction film
The Matrix -> publication date -> 1999
关系由明确 property 表达。
```

所以：

- Obsidian 适合个人知识组织和观点沉淀；
- Wikidata 适合公共实体关系、消歧、多语言名称、时间线和批量查询；
- Wikipedia/Fandom/官方 Wiki 适合提供解释、叙事和细节上下文。

## 安装方式

### Hermes Agent

把本项目放到 Hermes skills 目录，例如：

```bash
mkdir -p ~/.hermes/skills/research/wiki-research
cp SKILL.md ~/.hermes/skills/research/wiki-research/SKILL.md
```

然后在新 Hermes session 中按需加载：

```text
/skill wiki-research
```

或者在对话中明确说：

```text
请用 wiki-research 先建立这个主题的 wiki-source baseline。
```

### Codex / 其他支持 Agent Skills 的工具

将 `SKILL.md` 放到对应 agent 的 skills 目录或项目级 `.agents/skills/wiki-research/SKILL.md`。不同工具的 skill 发现机制不同，请按对应工具文档处理。

对于 Codex，建议优先作为**项目级 skill**使用，而不是全局安装，除非你经常做 wiki/lore/知识图谱相关研究工具。

## 推荐 Prompt 示例

### 1. 娱乐/IP/lore 研究

```text
Use wiki-research to map the wiki-source baseline for this franchise: official wiki, Fandom/community wiki, Wikipedia/Wikidata, major lore pages, canon status, character/faction/timeline structure, and reliability caveats. Do not do full market research yet.
```

中文：

```text
用 wiki-research 先为这个 IP 建立 wiki 信息源基线：官方 Wiki、Fandom/社区 Wiki、Wikipedia/Wikidata、主要 lore 页面、canon 状态、角色/势力/时间线结构和可靠性注意事项。暂时不要展开完整市场研究。
```

### 2. 与深度研究 skill 配合

```text
Before running the deep research skill, use wiki-research as a narrow routing step: identify useful wiki-style sources, entity aliases, relationship graph candidates, and claims that must be verified with current/primary sources.
```

中文：

```text
在运行深度研究 skill 前，先把 wiki-research 当作一个窄的路由步骤：识别有用的 wiki-style 来源、实体别名、关系图谱候选，以及必须用当前/一手来源验证的 claims。
```

### 3. Wikidata / 关系图谱

```text
Use wiki-research to decide whether Wikidata is useful for this topic. If useful, extract candidate entities, aliases, typed relationships, dates, and multilingual names. Explain which parts need article/wiki context rather than graph data.
```

中文：

```text
用 wiki-research 判断 Wikidata 是否适合这个主题。如果适合，提取候选实体、别名、类型化关系、日期和多语言名称，并说明哪些部分需要回到文章/wiki 语境解释，不能只看图谱数据。
```

### 4. 当前事实限制

```text
Use wiki-research only for stable background and entity/lore mapping. For current product status, pricing, policy, market size, revenue, or funding, explicitly switch to current web/official sources.
```

中文：

```text
wiki-research 只用于稳定背景和实体/lore 映射。涉及当前产品状态、价格、政策、市场规模、收入或融资时，必须明确切换到当前 web/官方来源。
```

## 项目结构

```text
wiki-research-skill/
├── SKILL.md       # Skill 主体
├── README.md      # 中文说明
├── README.en.md   # English README
├── LICENSE        # MIT
└── .gitignore
```

## 许可证

MIT
