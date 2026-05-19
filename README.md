# weread-researcher

> 从微信读书记录里，看见你自己。

`weread-researcher` / `weread-mirror` 是一个基于微信读书数据的 AI Skill。它不是普通的读书总结器，而是一个「个人认知研究员」：围绕微信读书的书架、已读、在读、想读、划线、笔记、想法、书评和阅读时间线，完成阅读复盘、单书分析、主题研究、深层自我洞察、多视角洞察、内容生产、知识库联动、阅读推荐、继续阅读计划，并导出一份好看的 HTML 报告。

## 核心闭环

```text
读过什么
→ 总结什么
→ 多视角洞察
→ 看见自己
→ 发现缺口
→ 推荐下一本
→ 继续阅读
→ 导出 HTML
```

## 总入口命令

```text
/weread-loop
/weread-loop 最近一周
/weread-loop 最近三个月
/weread-loop 2026年
/weread-loop AI Agent --lens decision --html
/weread-loop 独立开发 --lens content --html
/weread-loop 个人知识管理 --lens deep --html
```

默认行为：

```text
最近 30 天阅读记录
+ 默认洞察组合包
+ 下一本书推荐
+ 7 天继续阅读计划
+ HTML 报告
```

## 完整功能目录

```text
weread-mirror
├── 总控工作流
│   └── weread-loop
│       ├── 读过什么
│       ├── 总结什么
│       ├── 多视角洞察
│       ├── 看见自己
│       ├── 发现缺口
│       ├── 推荐下一本
│       ├── 继续阅读
│       └── 导出 HTML
├── 阅读汇总
│   ├── reading-daily
│   ├── reading-weekly
│   ├── reading-monthly
│   └── reading-yearly
├── 单书分析
│   ├── book-summary
│   ├── book-deepdive
│   ├── book-to-action
│   └── book-questions
├── 主题研究
│   ├── topic-map
│   ├── topic-compare
│   ├── reading-gap
│   └── learning-path
├── 深层自我洞察
│   ├── mind-journey
│   ├── core-pursuit
│   ├── ten-year-answer
│   ├── contradiction-check
│   ├── core-anxiety
│   ├── blind-spots
│   └── avoid-and-desire
├── 多视角洞察
│   ├── growth-evidence
│   ├── action-guide
│   ├── deep-questions
│   ├── theme-extension
│   ├── inner-assets
│   ├── contrarian-insights
│   ├── global-scan
│   ├── meaning-radar
│   ├── influence-map
│   ├── bottom-question
│   ├── acceptance-action
│   ├── blindspot-explore
│   ├── third-person-view
│   ├── life-script
│   ├── thought-trap-check
│   ├── personality-hints
│   ├── personal-flywheel
│   ├── core-conflict
│   ├── value-clarification
│   ├── inversion-thinking
│   ├── second-order-thinking
│   ├── munger-view
│   ├── aristotle-view
│   ├── seneca-view
│   └── eurich-view
├── 内容生产
│   ├── book-to-xhs
│   ├── book-to-wechat-article
│   ├── book-to-video-script
│   ├── book-to-cards
│   └── reading-series
├── 知识库联动
│   ├── export-book-to-obsidian
│   ├── book-to-atomic-notes
│   ├── build-topic-moc
│   └── book-to-project
├── 阅读推荐
│   ├── next-book
│   ├── recommend-by-goal
│   ├── recommend-by-gap
│   ├── recommend-for-question
│   ├── recommend-opposite
│   ├── recommend-topic
│   ├── recommend-for-content
│   ├── reading-roadmap
│   └── shelf-cleanup
└── 导出能力
    ├── export-reading-html
    ├── export-markdown
    ├── export-obsidian
    └── export-xhs
```

## 洞察组合包

| 组合 | 命令参数 | 包含视角 |
|---|---|---|
| 默认洞察 | `--lens default` | global-scan、meaning-radar、core-conflict、value-clarification、blindspot-explore、third-person-view、personal-flywheel、contrarian-insights |
| 深度自我洞察 | `--lens deep` | mind-journey、core-pursuit、ten-year-answer、contradiction-check、core-anxiety、blind-spots、avoid-and-desire |
| 决策洞察 | `--lens decision` | core-conflict、value-clarification、inversion-thinking、second-order-thinking、munger-view、aristotle-view、seneca-view、eurich-view |
| 内容创作洞察 | `--lens content` | theme-extension、contrarian-insights、influence-map、book-to-xhs、book-to-video-script、book-to-cards、reading-series |
| 复盘整理洞察 | `--lens review` | growth-evidence、action-guide、deep-questions、theme-extension、inner-assets、contrarian-insights、global-scan |
| 自我觉察洞察 | `--lens self` | meaning-radar、influence-map、bottom-question、acceptance-action、blindspot-explore、third-person-view、life-script、thought-trap-check、personality-hints |

## 推荐文件

- [`SKILL.md`](./SKILL.md)：Skill 主说明与执行规范
- [`commands/weread-loop.md`](./commands/weread-loop.md)：总控工作流实现说明
- [`commands/reading-summary.md`](./commands/reading-summary.md)：阅读汇总命令
- [`commands/book-analysis.md`](./commands/book-analysis.md)：单书分析命令
- [`commands/topic-research.md`](./commands/topic-research.md)：主题研究命令
- [`commands/deep-self-insight.md`](./commands/deep-self-insight.md)：深层自我洞察命令
- [`commands/multi-insight-lenses.md`](./commands/multi-insight-lenses.md)：多视角洞察命令
- [`commands/reading-recommendation.md`](./commands/reading-recommendation.md)：阅读推荐命令
- [`commands/content-and-knowledge-export.md`](./commands/content-and-knowledge-export.md)：内容生产与知识库联动
- [`prompts/insight-lenses.md`](./prompts/insight-lenses.md)：多视角洞察提示词模板
- [`templates/reading-loop-report.html`](./templates/reading-loop-report.html)：HTML 报告模板

## 设计原则

1. 不只总结书，而是理解用户长期阅读轨迹。
2. 不只推荐用户喜欢的书，也推荐能补缺口和打破舒适区的书。
3. 不做心理诊断，只做基于阅读材料的自我反思辅助。
4. 所有洞察必须基于划线、笔记、书评、阅读时间线等证据。
5. 输出要能沉淀为 Markdown、Obsidian 笔记、HTML 报告和自媒体内容。
