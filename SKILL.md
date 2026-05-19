# weread-researcher

## Purpose

`weread-researcher` is a WeRead-based personal cognition researcher skill. It turns WeRead reading data into a complete loop:

```text
读过什么 → 总结什么 → 多视角洞察 → 看见自己 → 发现缺口 → 推荐下一本 → 继续阅读 → 导出 HTML
```

The skill should rely on the official WeRead skill or any available WeRead data access layer for source data, then add higher-level analysis, workflow orchestration, insight lenses, recommendation logic, and export templates.

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

Answer:

- 最近读了哪些书
- 哪些书投入最多
- 哪些书真正击中用户
- 高频主题是什么
- 当前阅读状态是深读、泛读、囤书还是主题探索

### 2. 总结什么 / Reading Digest

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

- deep-self-review / 深度自我洞察
- mind-journey / 心路变化
- core-pursuit / 核心追求
- ten-year-answer / 十年答案
- core-anxiety / 核心焦虑
- avoid-and-desire / 逃避与渴望

Decision bundle:

- core-conflict / 当前张力
- value-clarification / 价值澄清
- inversion-thinking / 反向推演
- second-order-thinking / 二阶思考
- munger-view / 芒格视角
- seneca-view / 塞涅卡视角

Content bundle:

- theme-extension / 主题生长
- contrarian-insights / 反常识洞见
- influence-map / 影响力地图
- book-to-xhs / 小红书内容
- book-to-video-script / 短视频口播
- book-to-cards / 卡片内容

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

Find:

- 主题缺口
- 视角缺口
- 难度缺口
- 行动缺口
- 输出缺口
- 决策缺口

### 6. 推荐下一本 / Reading Recommendation

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

### 8. 导出 HTML / Export

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
