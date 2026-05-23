# Wiki Research Skill

[中文](README.md) | [English](README.en.md)

为 AI agent 的普通搜索和研究任务补充 wiki 类信息源。安装后，agent 应在相关场景中自动考虑 Wikipedia、Wikidata、官方/项目 Wiki、Fandom/社区 Wiki、MediaWiki 站点等来源，并在不相关时跳过。

## 特性

- 区分 Wikipedia、Wikidata、官方 Wiki、项目 Wiki、Fandom/社区 Wiki 与当前资料的使用边界。
- 适合娱乐/IP/lore、项目知识、实体关系、时间线、跨语言叙事差异等研究场景。
- 可嵌入已有 deep research、market research、competitive intelligence、KBS/Obsidian 工作流；不要求用户单独写复杂 prompt。
- 不绑定任何 MCP server 或外部依赖；可在 Hermes、Codex、Claude Code 等支持 `SKILL.md` 的 agent 中使用。

## 快速使用

安装后，用户不需要专门说“使用 wiki-research”。正常提出搜索或研究请求即可，例如：

```text
帮我研究一下《赛博朋克 2077》的世界观、主要势力和角色关系。
```

```text
查一下这个开源项目的发展背景、核心维护者和相关项目。
```

Agent 应根据任务自动判断是否需要调用 `wiki-research`：

- 相关时：把 Wikipedia、Wikidata、官方/项目 Wiki、Fandom/社区 Wiki 等来源纳入搜索。
- 有价值时：整理别名、实体关系、作品/角色/组织关系、lore/canon、时间线或社区分类。
- 输出时：简单标明信息来自官方、百科、社区维护来源，或仍需进一步验证。
- 不相关时：跳过，不打扰主研究流程。

## 适用场景

- 概念、人物、组织、地点、事件、作品、franchise 的背景梳理。
- 娱乐/IP 研究：lore、canon、角色关系、世界观、势力、道具、技能、剧情线、章节/任务/剧集级别细节。
- 查找某个领域是否存在官方 Wiki、项目 Wiki、Fandom、wiki.gg、Miraheze、MediaWiki 站点或其他社区知识库。
- 整理实体关系、别名、多语言名称、时间线、知识图谱候选。
- 比较不同语言 Wikipedia 或不同社区 Wiki 对同一主题的叙事差异。
- 在普通搜索或深度研究中补充术语、实体、相关页面和可靠性边界。

## 不适用场景

不要把 wiki 来源作为以下问题的主要依据：

- 最新新闻、融资、市场规模、价格、政策、法规、产品状态、API 当前行为。
- 法律、合规、财务或商业结论。
- 需要官方文档、论文、财报、行业报告、实时数据或一手来源的问题。
- 已由完整 deep research skill 主导的研究任务。

这些场景中，wiki 只适合作为背景、术语解释或实体消歧。

## 与已有研究 Skill 配合

`wiki-research` 不是一个需要用户手动启动的完整研究流程。它更像一条自动触发的搜索增强规则：当研究对象适合查 wiki 类资料时，agent 使用它补充来源和关系信息；当问题主要依赖新闻、市场数据、政策、价格、API 或官方文档时，agent 只把 wiki 当背景资料，或直接跳过。

推荐行为：

```text
普通研究/搜索流程继续负责问题拆解、搜索、证据判断、综合分析和输出。
wiki-research 只在相关时补充 wiki 类来源、别名、实体关系、lore/canon、时间线和可靠性提醒。
```

## 来源分层

| 来源类型 | 主要用途 | 注意事项 |
|---|---|---|
| Wikipedia | 通用背景、稳定事实、人物/公司/作品/事件基础信息 | 不足以支撑市场、法律、产品、价格或当前状态判断 |
| Wikidata | 结构化实体关系、别名、多语言名称、时间线、作品-人物-组织关系 | 适合图谱和消歧；解释性上下文仍需文章/wiki/一手来源 |
| 官方/项目 Wiki | 软件、游戏、协议、平台、项目知识、官方机制/canon | 注意版本、维护状态和更新时间 |
| Fandom/社区 Wiki | 娱乐/IP lore、角色、世界观、粉丝分类、长尾细节 | 区分官方 canon、社区整理、粉丝推测和过期内容 |
| 当前 web/news/reports | 最近变化、商业状态、市场数据、政策、价格、产品更新 | 不属于 wiki-research 的主职责，通常交给深度研究流程 |

## 安装与配置

### 推荐方式：安装后让 agent 自动匹配

把 `SKILL.md` 安装到 agent 的全局或项目级 skills 目录。对于支持自动技能匹配的 agent，用户正常提问即可，不需要在每次 prompt 里写“使用 wiki-research”。

项目级安装更适合团队或单个研究项目；全局安装适合经常做 IP、lore、实体关系、项目背景研究的用户。

### Hermes Agent

如果 Hermes 支持从 GitHub URL 安装 Skill，可直接使用仓库地址：

```bash
hermes skills install https://github.com/ghosTM55/wiki-research-skill
```

如果你的 Hermes 版本需要指向 `SKILL.md` 文件：

```bash
hermes skills install https://raw.githubusercontent.com/ghosTM55/wiki-research-skill/main/SKILL.md --name wiki-research
```

安装后开启新会话。通常不需要手动输入 `/skill wiki-research`；只有在调试、演示或想强制使用时才需要显式加载：

```text
/skill wiki-research
```

### Codex / Claude Code / 其他 Agent Skills 工具

把 `SKILL.md` 放到对应 agent 的全局或项目级 skills 目录。不同工具的自动触发机制不同：有的根据 skill description 自动匹配；有的需要在项目规则文件中补一句，例如“搜索/研究时可自动使用 wiki-research 补充 wiki 类来源”。

常见项目级结构：

```text
.agents/skills/wiki-research/SKILL.md
```

### 手动安装

```bash
mkdir -p ~/.hermes/skills/research/wiki-research
curl -L https://raw.githubusercontent.com/ghosTM55/wiki-research-skill/main/SKILL.md \
  -o ~/.hermes/skills/research/wiki-research/SKILL.md
```

## 使用示例

### 普通用户请求

```text
帮我研究一下这个 IP 的世界观、角色关系和社区讨论里常见的分类。
```

```text
查一下这个项目的背景、核心概念、相关组织和历史脉络。
```

### Agent 应自动补充的内容

```text
如果相关，自动查找 Wikipedia、Wikidata、官方/项目 Wiki、Fandom/社区 Wiki；
整理有用的别名、实体关系、lore/canon、时间线、社区分类和来源可靠性。
如果不相关，跳过 wiki 来源。
```

## 相关 Skill：ghost-research

[`ghost-research`](https://github.com/ghosTM55/ghost-research-skill) 是一个面向深度研究和 KBS/Obsidian 沉淀的横纵分析 Skill。它和 `wiki-research` 的关系是：

- `wiki-research`：轻量、自动，在普通搜索/研究中补充 wiki 类来源和关系信息。
- `ghost-research`：重型、完整，用横纵分析法产出结构化深度研究报告。

推荐配合方式：当用户发起深度研究时，`ghost-research` 可以作为主流程；如果研究对象涉及百科背景、实体关系、IP/lore/canon、项目 Wiki 或社区知识，`wiki-research` 在后台补充相关来源和关系线索即可。

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
