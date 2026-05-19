# weread-researcher

## Purpose

`weread-researcher` is a WeRead-based personal cognition researcher skill. It turns WeRead reading data into a complete loop:

```text
读过什么 → 总结什么 → 多视角洞察 → 看见自己 → 发现缺口 → 推荐下一本 → 继续阅读 → 导出 HTML
```

The skill should rely on the official WeRead skill or any available WeRead data access layer for source data, then add higher-level analysis, workflow orchestration, insight lenses, recommendation logic, content generation, knowledge export, and HTML report templates.

## Data Inputs

When available, collect and normalize:

- Bookshelf
- Finished books
- Currently reading books
- Want-to-read books
- Reading progress
- Reading duration
- Highlights
- Notes / thoughts
- Book reviews
- Reading timeline
- Tags or inferred topics

Always distinguish between:

- What the book says
- What the user highlighted
- What the user personally wrote
- What the assistant infers

## Complete Capability Map

```text
weread-mirror
├── 总控工作流
│   └── weread-loop
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

## Primary Command

### `/weread-loop`

Default behavior:

```text
Analyze recent 30 days of WeRead data, run the default insight lens bundle, recommend next books, create a 7-day reading plan, and export a polished HTML report.
```

Supported examples:

```text
/weread-loop
/weread-loop 最近一周
/weread-loop 最近三个月
/weread-loop 2026年
/weread-loop AI Agent --lens decision --html
/weread-loop 独立开发 --lens content --html
/weread-loop 个人知识管理 --lens deep --html
```

## Workflow

### 0. Collect reading data

Collect source data and produce a normalized reading dataset.

### 1. 读过什么 / Reading Summary

This stage can call:

- reading-daily
- reading-weekly
- reading-monthly
- reading-yearly

Answer:

- 最近读了哪些书
- 哪些书投入最多
- 哪些书真正击中用户
- 高频主题是什么
- 当前阅读状态是深读、泛读、囤书还是主题探索

### 2. 总结什么 / Reading Digest

This stage can call:

- book-summary
- book-deepdive
- book-to-action
- book-questions
- topic-map
- topic-compare

Extract:

- 核心观点
- 关键划线
- 用户自己的想法
- 可行动内容
- 可输出内容

### 3. 多视角洞察 / Insight Lenses

Run one lens bundle.

Default bundle:

- global-scan / 全局扫描
- meaning-radar / 动力雷达
- core-conflict / 当前张力
- value-clarification / 价值澄清
- blindspot-explore / 盲区探索
- third-person-view / 他者视角
- personal-flywheel / 个人飞轮
- contrarian-insights / 反常识洞见

Deep bundle:

- mind-journey / 心路变化
- core-pursuit / 核心追求
- ten-year-answer / 十年答案
- contradiction-check / 前后矛盾
- core-anxiety / 核心焦虑
- blind-spots / 思维盲区
- avoid-and-desire / 逃避与渴望

Review bundle:

- growth-evidence / 成长证据
- action-guide / 行动指南
- deep-questions / 深问自己
- theme-extension / 主题延伸
- inner-assets / 内在资源
- contrarian-insights / 反常识洞见
- global-scan / 全局扫描

Self-awareness bundle:

- meaning-radar / 动力雷达
- influence-map / 影响力地图
- bottom-question / 心底之问
- acceptance-action / 接纳与行动
- blindspot-explore / 盲区探索
- third-person-view / 他者视角
- life-script / 人生剧本
- thought-trap-check / 思维陷阱
- personality-hints / 人格线索

Decision bundle:

- personal-flywheel / 个人飞轮
- core-conflict / 当前张力
- value-clarification / 价值澄清
- inversion-thinking / 反向推演
- second-order-thinking / 二阶思考
- munger-view / 芒格视角
- aristotle-view / 亚里士多德视角
- seneca-view / 塞涅卡视角
- eurich-view / 塔莎·尤里奇视角

Content bundle:

- theme-extension / 主题生长
- contrarian-insights / 反常识洞见
- influence-map / 影响力地图
- book-to-xhs / 小红书内容
- book-to-video-script / 短视频口播
- book-to-cards / 卡片内容
- reading-series / 系列内容

### 4. 看见自己 / Self Mirror

Compress lens outputs into a user portrait:

- 当前的你
- 你真正关心什么
- 你真正追求什么
- 当前主要矛盾
- 隐藏焦虑
- 逃避与渴望
- 下一阶段问题

### 5. 发现缺口 / Gap Analysis

Can call:

- reading-gap
- recommend-by-gap

Find:

- 主题缺口
- 视角缺口
- 难度缺口
- 行动缺口
- 输出缺口
- 决策缺口

### 6. 推荐下一本 / Reading Recommendation

Can call:

- next-book
- recommend-by-goal
- recommend-by-gap
- recommend-for-question
- recommend-opposite
- recommend-topic
- recommend-for-content
- reading-roadmap
- shelf-cleanup

Recommend a set, not just one book:

- 最该读的一本
- 补缺口的一本
- 反向挑战一本
- 内容输出一本
- 轻松过渡一本

Each recommendation must include:

- Why now
- Which previous notes or themes it connects to
- How to read it
- What to do after reading

### 7. 继续阅读 / Reading Plan

Create a 7-day reading plan:

- 每天读什么
- 带着什么问题读
- 重点章节
- 笔记任务
- 输出任务
- 下次复盘时间

### 8. 导出 / Export

Can call:

- export-reading-html
- export-markdown
- export-obsidian
- export-xhs
- export-book-to-obsidian
- book-to-atomic-notes
- build-topic-moc
- book-to-project

Generate a polished HTML report using `templates/reading-loop-report.html` as the base style.

## Safety and Tone

This skill may infer anxiety, avoidance, desire, and cognitive bias from reading notes. Keep the tone careful and non-diagnostic.

Use phrases such as:

- “从你的笔记看，可能……”
- “这更像是一种倾向，而不是结论。”
- “以下分析只用于自我反思，不等同于心理诊断。”

Avoid:

- Clinical diagnosis
- Deterministic personality labeling
- Overconfident claims about the user
- Making unsupported claims without referencing reading evidence

## Output Requirements

For every major insight, include:

1. Insight summary
2. Supporting evidence from reading data
3. Interpretation
4. Possible blind spot
5. Suggested next action

Prefer concise, structured Markdown for normal responses. Use HTML only when the user asks for export or when `/weread-loop --html` is invoked.
