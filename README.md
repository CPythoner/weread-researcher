# weread-researcher

> 从微信读书记录里，看见你自己。

`weread-researcher` / `weread-mirror` 是一个基于微信读书数据的 AI Skill。它不是普通的读书总结器，而是一个「个人认知研究员」：围绕微信读书的书架、已读、在读、想读、划线、笔记、想法、书评和阅读时间线，完成阅读复盘、主题研究、自我洞察、缺口分析、阅读推荐、继续阅读计划，并导出一份好看的 HTML 报告。

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

## 功能模块

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
├── 洞察组合包
│   ├── default 默认洞察
│   ├── deep 深度自我洞察
│   ├── decision 决策洞察
│   └── content 内容创作洞察
├── 阅读推荐
│   ├── next-book
│   ├── recommend-by-goal
│   ├── recommend-by-gap
│   ├── recommend-opposite
│   └── reading-roadmap
└── 导出能力
    ├── export-reading-html
    ├── export-markdown
    ├── export-obsidian
    └── export-xhs
```

## 多视角洞察

默认执行 8 个洞察镜头：

| 洞察 | 作用 |
|---|---|
| 全局扫描 | 从全部阅读记录里发现隐藏主线 |
| 动力雷达 | 分析真正驱动你的东西 |
| 当前张力 | 找出当下最核心的矛盾 |
| 价值澄清 | 看清真正重视什么 |
| 盲区探索 | 找出你没看到但重要的问题 |
| 他者视角 | 像朋友一样观察你的阅读和状态 |
| 个人飞轮 | 找出优势、积累和正反馈 |
| 反常识洞见 | 提炼最不寻常、最有传播价值的观点 |

## 推荐文件

- [`SKILL.md`](./SKILL.md)：Skill 主说明与执行规范
- [`commands/weread-loop.md`](./commands/weread-loop.md)：总控工作流实现说明
- [`prompts/insight-lenses.md`](./prompts/insight-lenses.md)：多视角洞察提示词模板
- [`templates/reading-loop-report.html`](./templates/reading-loop-report.html)：HTML 报告模板

## 设计原则

1. 不只总结书，而是理解用户长期阅读轨迹。
2. 不只推荐用户喜欢的书，也推荐能补缺口和打破舒适区的书。
3. 不做心理诊断，只做基于阅读材料的自我反思辅助。
4. 所有洞察必须基于划线、笔记、书评、阅读时间线等证据。
5. 输出要能沉淀为 Markdown、Obsidian 笔记、HTML 报告和自媒体内容。
