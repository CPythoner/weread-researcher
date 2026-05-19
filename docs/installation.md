# 安装与配置

本文说明如何安装 `weread-researcher`，以及如何配置底层 WeRead Skill / 微信读书数据访问能力。

## 1. 角色说明

`weread-researcher` 本身不是微信读书客户端，也不直接托管你的账号凭证。它是一个上层分析 Skill，负责：

- 阅读汇总
- 单书分析
- 主题研究
- 深层自我洞察
- 多视角洞察
- 阅读推荐
- 继续阅读计划
- HTML / Markdown / Obsidian 导出

微信读书数据建议由底层 WeRead Skill 提供。你可以理解成：

```text
WeRead Skill / 数据源
负责读取微信读书数据

weread-researcher
负责分析、洞察、推荐和导出
```

推荐目录结构：

```text
.codebuddy/skills/
├── weread/                 # 底层微信读书数据 Skill
└── weread-researcher/      # 本项目：分析层 Skill
```

## 2. 安装 weread-researcher

在你的项目目录中执行：

```bash
git clone https://github.com/CPythoner/weread-researcher.git
mkdir -p .codebuddy/skills
cp -r weread-researcher .codebuddy/skills/
```

最终目录应类似：

```text
<your-project>/
└── .codebuddy/
    └── skills/
        └── weread-researcher/
            ├── SKILL.md
            ├── README.md
            ├── commands/
            ├── prompts/
            └── templates/
```

如果你的 Agent / IDE 使用的是其他 skills 目录，请将 `weread-researcher` 放到对应位置。关键是让工具能加载到 `SKILL.md`。

## 3. 安装底层 WeRead Skill

`weread-researcher` 需要能够访问微信读书数据。底层 WeRead Skill 至少需要提供这些数据能力：

| 数据 | 用途 |
|---|---|
| 书架 | 判断长期兴趣和主题分布 |
| 已读 | 分析完成阅读和知识结构 |
| 在读 | 判断近期关注点 |
| 想读 | 判断潜在兴趣和未满足需求 |
| 划线 | 提取真正击中用户的观点 |
| 笔记 / 想法 | 分析用户自己的表达和困惑 |
| 书评 | 判断对整本书的理解 |
| 阅读进度 | 判断投入程度 |
| 阅读时间线 | 分析心路变化和阶段迁移 |

如果底层 Skill 的名称不是 `weread`，可以在 `.env` 中通过 `WEREAD_DATA_SOURCE` 标记实际数据源。

## 4. 配置环境变量

复制示例配置：

```bash
cp .env.example .env
```

填写：

```bash
WEREAD_API_KEY=wrk-your-api-key
WEREAD_DATA_SOURCE=official-skill
WEREAD_DEFAULT_RANGE=30d
WEREAD_DEFAULT_LENS=default
WEREAD_EXPORT_DIR=exports
```

字段说明：

| 字段 | 说明 |
|---|---|
| `WEREAD_API_KEY` | 微信读书 Agent / API Key，具体以你使用的数据源要求为准 |
| `WEREAD_DATA_SOURCE` | 数据来源，例如 `official-skill`、`local-json`、`custom-api` |
| `WEREAD_DEFAULT_RANGE` | 默认分析范围，例如 `7d`、`30d`、`90d`、`year` |
| `WEREAD_DEFAULT_LENS` | 默认洞察组合，例如 `default`、`deep`、`decision`、`content` |
| `WEREAD_EXPORT_DIR` | 报告导出目录 |

## 5. 获取 WeRead API Key

如果你使用的是官方微信读书 Agent / Skill 数据能力，通常需要在微信读书 App 中生成个人 API Key。

入口可能会随 App 版本变化，一般可在以下位置附近查找：

```text
微信读书 App
→ 我
→ 设置
→ 账号、安全或 Agent 相关设置
→ 生成 / 复制 API Key
```

Key 通常是个人私有凭证。请注意：

- 不要把真实 Key 写进 README
- 不要把 `.env` 提交到 Git
- 不要把 Key 发到公开 Issue、PR 或截图里
- 如果怀疑泄露，立即在微信读书内重新生成或撤销

## 6. 使用本地 JSON 数据源

如果暂时没有接入官方 WeRead Skill，也可以先用本地 JSON 做调试。

`.env` 示例：

```bash
WEREAD_DATA_SOURCE=local-json
WEREAD_LOCAL_DATA=examples/sample-reading-data.json
```

建议本地数据结构：

```json
{
  "books": [],
  "highlights": [],
  "notes": [],
  "reviews": [],
  "timeline": []
}
```

这样可以先验证 `/weread-loop` 的分析、推荐和 HTML 导出逻辑。

## 7. 验证安装

在 Agent 对话中输入：

```text
/weread-loop 最近一周 --lens default --html
```

如果正常，应该能看到：

```text
1. 阅读概览
2. 核心观点
3. 多视角洞察
4. 自我画像
5. 阅读缺口
6. 下一本书推荐
7. 7 天继续阅读计划
8. HTML 报告
```

也可以单独测试：

```text
/reading-weekly
/book-summary 《某本书》
/topic-map 个人知识管理
/next-book
```

## 8. 常见问题

### 8.1 找不到微信读书数据

检查：

- 底层 WeRead Skill 是否安装
- `WEREAD_API_KEY` 是否配置
- `WEREAD_DATA_SOURCE` 是否与实际数据源一致
- Agent 是否重新加载 skills

### 8.2 HTML 没有生成

检查：

- 是否使用 `--html`
- `WEREAD_EXPORT_DIR` 是否存在或可写
- `templates/reading-loop-report.html` 是否存在

### 8.3 洞察太空泛

解决：

- 增加时间范围，例如最近三个月或一年
- 优先使用有笔记和书评的数据
- 让命令输出“阅读证据”
- 使用更具体的主题，例如 `/weread-loop 独立开发 --lens deep`

### 8.4 分析像心理诊断

本项目要求所有深层洞察都使用谨慎表达。可以在提示中加入：

```text
请只做基于阅读材料的自我反思，不要做心理诊断；所有推断都要写“可能”“倾向于”“从笔记看”。
```

## 9. 安全建议

`.gitignore` 应至少包含：

```gitignore
.env
exports/
*.html
*.png
*.jpg
*.jpeg
*.webp
```

如果你要保存导出的 HTML 报告，建议放到私有目录；报告可能包含个人阅读记录、笔记、焦虑、追求、盲区等敏感内容。
