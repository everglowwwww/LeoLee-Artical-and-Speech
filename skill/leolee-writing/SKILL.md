---
name: leolee-writing
description: "Generate academic papers and presentation speeches following LeoLee's personal writing standards. Uses a multi-round conversational workflow to determine topic, outline, structure, and references before generating the final document."
---

# LeoLee Writing  v1.1 — 多轮对话工作流

学术论文与演讲写作助手。采用多轮对话方式逐步确定内容，每轮确认后再推进，确保最终产出符合需求。

## When to Use

### Must Use
- Writing a course paper, thesis report, literature review, or journal article
- Formatting a Word document with specific font/spacing/margin needs
- Writing slide-by-slide speaker notes for an academic presentation (defense, final report, conference)
- Reviewing a paper draft for reference integrity and structural correctness

### Recommended
- The paper needs bilingual (Chinese + English) abstract
- The paper involves cross-disciplinary content
- Reference accuracy is critical and no fabrication is allowed

### Skip
- Pure code generation with no academic writing
- Casual or non-academic content

---

## Menu

When invoked, present this menu:

```
╔════════════════════════════════════════════╗
║  LeoLee Writing  v1.1                     ║
║  多轮对话 · 逐步确认 · 精准输出          ║
╠════════════════════════════════════════════╣
║                                            ║
║  [1] 📄 论文写作                           ║
║      5 轮对话：主题 → 文献 → 大纲          ║
║      → 内容审核 → 生成                    ║
║                                            ║
║  [2] 🎤 演讲稿写作                         ║
║      4 轮对话：情境 → 弧线 → 幻灯片        ║
║      → 生成                                ║
║                                            ║
╚════════════════════════════════════════════╝
```

---

## [1] 论文写作 — 5 轮对话工作流

### Round 1：主题与范围

目标和产出：明确论文的主题、角度、类型和篇幅。

对话内容：
- 论文主题是什么？（一个句子概括）
- 具体的研究角度或切入点是什么？
- 论文类型：课程论文 / 结题报告 / 综述 / 期刊论文
- 预计字数/页数
- 语言：中文（保留英文术语） / 纯英文
- 格式变体：标准格式（17pt+3.17cm） / 短篇格式（25pt+1.91cm）

在此轮结束时，向用户复述确认：
```
📋 论文概要确认
────────────────────
主题：{用户确认的题目}
类型：{课程论文}
角度：{具体切入点}
字数：{约3000字}
语言：{中文}
格式：{标准格式}
────────────────────
以上是否正确？下一步我将搜索相关参考文献。
```

---

### Round 2：文献检索

目标和产出：确定论文的参考文献列表。

对话逻辑：
1. 询问用户是否已有参考文献列表
2. 如果有 → 用户提供列表，核实格式
3. 如果没有 → 告知用户我将联网搜索真实文献
4. 搜索文献 → 通过 OpenAlex 或类似学术 API 搜索 5-10 篇相关文献
5. 将搜索结果整理成列表（含标题、作者、期刊、年份、DOI）
6. 呈现给用户确认：
```
📚 候选参考文献
────────────────────
[1] {作者}. {标题}[J]. {期刊}, {年份}.
    DOI: {doi}
[2] ...
────────────────────
以上文献可以接受吗？
- 需要增减某些文献？
- 需要更换某些主题方向的文献？
```

7. 根据用户反馈调整文献列表

---

### Round 3：大纲生成

目标和产出：确定论文的章节结构和每节要点。

对话逻辑：
1. 根据 Round 1 的主题和 Round 2 的文献，生成论文大纲草案
2. 呈现给用户：
```
📑 论文大纲草案
────────────────────
标题：{生成标题}

1 引言
  要点：{背景} → {问题} → {论文目的}

2 {主体章节1}
  2.1 {子节1}
  2.2 {子节2}

3 {主体章节2}
  3.1 {子节1}
  3.2 {子节2}

X 结语

参考文献：{N}篇
────────────────────
以上结构是否合适？
- 需要调整章节顺序？
- 需要增删某节？
- 某个要点需要重新聚焦？
```

3. 根据用户反馈调整大纲

---

### Round 4：内容逐节确认

目标和产出：对每节的详细内容达成一致。

对话逻辑：逐节与用户讨论内容：
```
📝 逐节内容确认 — 第 X 轮
────────────────────
当前节：{章节名}

我计划在本节涵盖：
1. {要点1}
2. {要点2}
3. {要点3} → 引用文献 [{N}]

你希望调整、补充或删减哪些内容？
```

每次确认一节或一组相关节（视复杂程度而定），然后进入下一节。

---

### Round 5：生成与审阅

目标和产出：生成格式规范的 .docx 文件供用户审阅。

流程：
1. 根据前 4 轮所有确认内容，使用 python-docx 生成论文
2. 文件命名格式：{论文主题}_课程论文_李沛霖.docx
3. 输出到用户指定的目录
4. 告知用户文件已生成，并询问是否需要修改

修改循环：
- 用户可以提出具体修改意见（增删改某段、调整引用等）
- 修改后重新生成
- 直到用户满意为止

---

### 论文格式规范

（保持不变）

#### 页面设置

```
上边距：2.54 cm
下边距：2.54 cm
左边距：3.17 cm（标准）/ 1.91 cm（短篇）
右边距：3.17 cm（标准）/ 1.91 cm（短篇）
```

#### 字体层级

| 层级 | 字体 | 字号 | 字重 | 对齐 | 行距 |
|---|---|---|---|---|---|
| 中文标题 | 华文中宋 | 18pt | Bold | 居中 | 固定值 17pt |
| 英文标题 | Times New Roman | 14pt | Normal | 居中 | 固定值 17pt |
| 摘要/正文 | 宋体 | 10.5pt (5号) | Normal | 两端对齐 | 固定值 17pt |
| 一级章节标题 | 宋体 | 12pt | Bold | 左对齐缩进24pt | 固定值 17pt |
| 二级章节标题 | 宋体 | 10.5pt | Bold | 左对齐缩进21pt | 固定值 17pt |
| 英文/数字 | Times New Roman | 10.5pt | Normal | 行内嵌入 | 固定值 17pt |
| 图注 | 宋体 | — | Normal | 居中缩进0pt | 固定值 17pt |
| 参考文献 | Times New Roman | — | Normal | 左对齐缩进0pt | 固定值 17pt |

#### 段落格式

| 类型 | 首行缩进 | 段前距 | 段后距 |
|---|---|---|---|
| 正文段落 | 21pt | 4pt | 0pt |
| 章节标题 | 24pt | 7.8pt | 7.8pt |
| 图注/参考文献 | 0pt | 4pt | 0pt |

#### 结构模板

```
论文标题（华文中宋 18pt）
英文标题（Times New Roman 14pt）

摘要：xxx（宋体 10.5pt）
关键词：xxx；xxx；xxx

Abstract: xxx
Keywords: xxx

0/1 引言
  正文段落（宋体 10.5pt，首行缩进21pt，行距固定17pt）
  1.1 子标题
    正文段落...

2 章节标题
  2.1 子标题
    ...

X 结语

参考文献
[1] 作者. 标题[D/J]. 出版地：出版社, 年份.
[2] Author. Title[J]. Journal Name, Year.
```

#### 各章节写作规则

##### 引言
- 第一段：交代研究背景，指出核心需求或矛盾
- 第二段：描述技术/方法发展现状，用引用佐证
- 第三段：明确本文研究目标、方法和结构概述
- 涉及跨学科时，诚实地说明自己的学科背景和局限
- 引言通常包含 3-6 个引用

##### 主体章节
- 每节写一个技术维度或分析维度的内容
- 每节内部：首段总述 → 子节逐项展开
- 每个子节至少：定义/原理 → 优势 → 局限/问题 → (示例/引用)
- 引用应编织进句子中，而非独立括号
- 图/表格式：图[序号] 图注内容 作者. 来源
- 英文专业术语在中文正文中保留英文原文

##### 结语
- 总结主要发现和结论
- 指出研究意义和贡献
- 客观列出局限
- 展望未来方向
- 语气学术、客观

#### 参考文献规范

```
中文书籍：  [序号] 作者. 书名[M]. 出版地：出版社, 年份.
中文期刊：  [序号] 作者. 文章名[J]. 期刊名, 年份(期号): 页码.
学位论文：  [序号] 作者. 论文名[D]. 出版地：大学名, 年份.
英文文献：  [序号] Author. Title[J]. Journal Name, Year, Volume: Pages.
网页来源：  [序号] 标题[EB/OL]. URL, 访问日期.

🔴 铁律：不得虚构任何参考文献
🔴 铁律：不确定的引用用 [待补充] 标记，让用户确认
🔴 铁律：英文术语必须使用 Times New Roman 字体
```

---

## [2] 演讲稿写作 — 4 轮对话工作流

### Round 1：情境收集

对话内容：
- 场合：开题答辩 / 期末汇报 / 学术会议
- 演讲题目
- 时长要求
- 听众背景（专业/非专业、导师/同学等）
- 语言：中文 / 英文
- 是否已有 .pptx 文件？
- 输出目录

### Round 2：叙事弧线确认

对话内容：
```
🎯 叙事弧线草案
────────────────────
开篇（如何入题）：
  {草案}

中段（核心论点/转折）：
  {草案}

结尾（听众应该带走什么）：
  {草案}
────────────────────
以上叙事方向是否合适？
```

### Round 3：幻灯片审阅（如有 .pptx）

如有 .pptx 文件：
1. 运行 scripts/read_slides.py 提取内容
2. 运行 scripts/render_slides.py 渲染为 PNG
3. 生成理解摘要呈现给用户确认

如无 .pptx 文件：
- 跳过此轮，直接进入 Round 4

### Round 4：生成与注入

1. 逐页撰写讲稿
2. 注入 PPTX 备注栏或生成 .docx 排练文稿
3. 输出到指定目录

---

## Scripts

This skill includes Python scripts from the speaker skill (AI272/speaker) for PPT speech writing:

- `scripts/read_slides.py`
- `scripts/render_slides.py`
- `scripts/visual_inventory.py`
- `scripts/vision_review.py`
- `scripts/inject_notes.py`
- `scripts/write_display_docx.py`
