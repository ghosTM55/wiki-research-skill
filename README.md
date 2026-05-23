# Wiki Research Skill

[中文](README.md) | [English](README.en.md)

面向 AI agent 的 wiki 信息源路由 Skill：帮助 agent 在研究任务中判断何时使用 Wikipedia、Wikidata、官方/项目 Wiki、Fandom/社区 Wiki、MediaWiki 站点，以及何时切换到当前 web、官方文档或深度研究流程。

## 特性

- 区分 Wikipedia、Wikidata、官方 Wiki、项目 Wiki、Fandom/社区 Wiki 与当前资料的使用边界。
- 适合娱乐/IP/lore、项目知识、实体关系、时间线、跨语言叙事差异等研究场景。
- 可作为已有 deep research、market research、competitive intelligence、KBS/Obsidian ingest 等技能的前置 source-routing layer。
- 不绑定任何 MCP server 或外部依赖；可在 Hermes、Codex、Claude Code 等支持 `SKILL.md` 的 agent 中使用。

## 快速使用

在你的 AI agent 中安装或引用这个 Skill 后，可以这样提示：

```text
Use wiki-research to establish the wiki-source baseline for this topic: relevant Wikipedia/Wikidata pages, official/project wikis, Fandom/community wikis, entity aliases, lore/canon structure, relationship graph candidates, and reliability notes. Then continue with my existing deep research workflow for current sources and analysis.
```

中文提示：

```text
使用 wiki-research 为这个主题建立 wiki 信息源基线：相关 Wikipedia/Wikidata 页面、官方/项目 Wiki、Fandom/社区 Wiki、实体别名、lore/canon 结构、关系图谱候选和可靠性说明。之后继续使用我已有的深度研究流程处理当前资料和分析判断。
```

## 适用场景

- 概念、人物、组织、地点、事件、作品、franchise 的背景梳理。
- 娱乐/IP 研究：lore、canon、角色关系、世界观、势力、道具、技能、剧情线、章节/任务/剧集级别细节。
- 查找某个领域是否存在官方 Wiki、项目 Wiki、Fandom、wiki.gg、Miraheze、MediaWiki 站点或其他社区知识库。
- 整理实体关系、别名、多语言名称、时间线、知识图谱候选。
- 比较不同语言 Wikipedia 或不同社区 Wiki 对同一主题的叙事差异。
- 在深度研究前建立术语、实体、来源地图和可靠性边界。

## 不适用场景

不要把 wiki 来源作为以下问题的主要依据：

- 最新新闻、融资、市场规模、价格、政策、法规、产品状态、API 当前行为。
- 法律、合规、财务或商业结论。
- 需要官方文档、论文、财报、行业报告、实时数据或一手来源的问题。
- 已由完整 deep research skill 主导的研究任务。

这些场景中，wiki 只适合作为背景、术语解释或实体消歧。

## 与已有研究 Skill 配合

`wiki-research` 不应该替代已有研究 Skill。它的职责是前置路由和信息源分层。

```text
wiki-research 负责：
- 判断是否需要 wiki-style sources
- 选择 Wikipedia / Wikidata / 官方 Wiki / Fandom / 社区 Wiki
- 提取实体、别名、lore/canon 结构、关系图谱候选
- 标注来源可靠性和需要进一步验证的 claims

主研究 Skill 负责：
- 问题拆解
- 广泛搜索
- 证据评估
- 综合分析
- 报告结构
- KBS/Obsidian 写入
```

推荐组合方式：

```text
First use wiki-research as a source-routing step. Keep the output compact and structured. Then pass the wiki-source baseline into the active deep research skill.
```

## 来源分层

| 来源类型 | 主要用途 | 注意事项 |
|---|---|---|
| Wikipedia | 通用背景、稳定事实、人物/公司/作品/事件基础信息 | 不足以支撑市场、法律、产品、价格或当前状态判断 |
| Wikidata | 结构化实体关系、别名、多语言名称、时间线、作品-人物-组织关系 | 适合图谱和消歧；解释性上下文仍需文章/wiki/一手来源 |
| 官方/项目 Wiki | 软件、游戏、协议、平台、项目知识、官方机制/canon | 注意版本、维护状态和更新时间 |
| Fandom/社区 Wiki | 娱乐/IP lore、角色、世界观、粉丝分类、长尾细节 | 区分官方 canon、社区整理、粉丝推测和过期内容 |
| 当前 web/news/reports | 最近变化、商业状态、市场数据、政策、价格、产品更新 | 不属于 wiki-research 的主职责，通常交给深度研究流程 |

## 安装

### Hermes Agent

如果 Hermes 支持从 GitHub URL 安装 Skill，可直接使用仓库地址：

```bash
hermes skills install https://github.com/ghosTM55/wiki-research-skill
```

如果你的 Hermes 版本需要指向 `SKILL.md` 文件：

```bash
hermes skills install https://raw.githubusercontent.com/ghosTM55/wiki-research-skill/main/SKILL.md --name wiki-research
```

安装后开启新会话，并按需加载：

```text
/skill wiki-research
```

### Codex / Claude Code / 其他 Agent Skills 工具

把 `SKILL.md` 安装到对应 agent 的全局或项目级 skills 目录。推荐项目级安装，避免全局过度触发。

常见项目级结构：

```text
.agents/skills/wiki-research/SKILL.md
```

不同 agent 的安装命令和目录不同，请以对应工具文档为准。

### 手动安装

```bash
mkdir -p ~/.hermes/skills/research/wiki-research
curl -L https://raw.githubusercontent.com/ghosTM55/wiki-research-skill/main/SKILL.md \
  -o ~/.hermes/skills/research/wiki-research/SKILL.md
```

## 推荐 Prompt

### 娱乐/IP/lore

```text
Use wiki-research to map the wiki-source baseline for this franchise: official wiki, Fandom/community wiki, Wikipedia/Wikidata, major lore pages, canon status, character/faction/timeline structure, and reliability caveats. Do not do full market research yet.
```

### 配合深度研究

```text
Before running the deep research skill, use wiki-research as a narrow routing step: identify useful wiki-style sources, entity aliases, relationship graph candidates, and claims that must be verified with current/primary sources.
```

### 当前事实边界

```text
Use wiki-research only for stable background and entity/lore mapping. For current product status, pricing, policy, market size, revenue, or funding, explicitly switch to current web/official sources.
```

## 仓库结构

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
