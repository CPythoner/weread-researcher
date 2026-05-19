# 内容生产与知识库联动命令

## 模块目标

把微信读书笔记转成公开内容、知识库条目和项目行动。

## 内容生产命令

```text
/book-to-xhs 《书名或主题》
/book-to-wechat-article 《书名或主题》
/book-to-video-script 《书名或主题》
/book-to-cards 《书名或主题》
/reading-series 主题 期数
```

### `/book-to-xhs`

输出：

```markdown
# 小红书图文内容

## 1. 标题备选
## 2. 正文
## 3. 标签
## 4. 图片页规划
## 5. 评论区引导
```

### `/book-to-wechat-article`

输出：

```markdown
# 公众号文章

## 1. 标题
## 2. 100-120 字摘要
## 3. 文章大纲
## 4. 正文
## 5. 结尾问题
```

### `/book-to-video-script`

输出：

```markdown
# 短视频口播

## 1. 30 秒版
## 2. 90 秒版
## 3. 3 分钟版
## 4. 分镜建议
## 5. 标题和标签
```

### `/book-to-cards`

输出：

```markdown
# 知识卡片

## 1. 封面卡
## 2. 观点卡
## 3. 金句卡
## 4. 行动卡
## 5. 总结卡
```

### `/reading-series`

输出：

```markdown
# 阅读系列内容

## 1. 系列定位
## 2. 每期标题
## 3. 每期核心观点
## 4. 对应书籍 / 笔记
## 5. 发布顺序
```

## 知识库联动命令

```text
/export-book-to-obsidian 《书名》
/book-to-atomic-notes 《书名》
/build-topic-moc 主题
/book-to-project 《书名》
```

### `/export-book-to-obsidian`

输出 Markdown：

```markdown
# 《书名》阅读笔记

## 一句话总结
## 核心观点
## 我的划线
## 我的想法
## 行动清单
## 相关概念
## 相关书籍
## 相关项目
```

### `/book-to-atomic-notes`

从一本书中提取可复用概念，生成多个原子笔记：

```text
40_知识库/长期主义.md
40_知识库/复利效应.md
40_知识库/安全边际.md
40_知识库/控制二分法.md
```

### `/build-topic-moc`

输出：

```markdown
# {{topic}} MOC

## 核心概念
## 相关书籍
## 相关笔记
## 相关项目
## 可继续研究的问题
```

### `/book-to-project`

把一本书变成一个可执行项目：

```markdown
# 阅读项目：{{book}}

## Context
## Actions
## Progress
## Success Metrics
## Related Notes
```

## 导出能力

```text
/export-reading-html
/export-markdown
/export-obsidian
/export-xhs
```

## 质量要求

- 内容生产要保留用户自己的判断，不要只复述书。
- 知识库导出要适合 Obsidian 双向链接。
- 生成项目时要包含可执行任务和成功指标。
- HTML 导出使用 `templates/reading-loop-report.html`。
