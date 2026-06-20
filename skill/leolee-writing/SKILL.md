---
name: leolee-writing
description: "Generate academic papers and presentation speeches following LeoLee's personal writing standards: formatting, structure, citation rules, and speech-writing workflow. Use when writing, revising, or formatting course papers, thesis reports, literature reviews, or creating slide-by-slide speaker notes for academic presentations."
---

# LeoLee Writing  v1.0

学术论文与演讲写作助手。严格遵循 LeoLee 的写作规范：格式、结构、引用、语言风格。

## When to Use

### Must Use

- Writing a course paper, thesis report, literature review, or journal article
- Formatting a Word document with specific font/spacing/margin needs  
- Writing slide-by-slide speaker notes for an academic presentation (defense, final report, conference)
- Reviewing a paper draft for reference integrity and structural correctness

### Recommended

- The paper needs bilingual (Chinese + English) abstract
- The paper involves cross-disciplinary content (architecture + urban planning + technology)
- Reference accuracy is critical and no fabrication is allowed

### Skip

- Pure code generation with no academic writing
- Casual or non-academic content

---

## Menu

When invoked, present this menu and wait for selection:

```
╔════════════════════════════════════════════╗
║  LeoLee Writing  v1.0                     ║
║  学术论文与演讲写作助手                    ║
╠════════════════════════════════════════════╣
║                                            ║
║  [1] 论文写作                              ║
║      课程论文 · 结题报告 · 综述 · 期刊     ║
║                                            ║
║  [2] 演讲稿写作                            ║
║      开题答辩 · 期末汇报 · 学术会议        ║
║                                            ║
╚════════════════════════════════════════════╝
```

After the user selects, proceed to the corresponding workflow. If the user provides a topic directly without selecting, analyze the request and auto-route to the appropriate mode.

---

## [1] 论文写作模块

### 1.1 收集需求

When entering paper mode, ask:

1. 论文类型：课程论文 / 结题报告 / 综述 / 期刊论文
2. 论文主题/题目
3. 语言：中文（保留英文术语） / 纯英文
4. 格式变体：标准格式（17pt行距+3.17cm边距） / 短篇格式（25pt行距+1.91cm边距）
5. 是否已有参考文献列表？(Y/N) — 如果没有，**必须询问用户提供**，不得自行编造
6. 输出目录：默认输出到指定的工作目录

### 1.2 页面设置

```
上边距：2.54 cm
下边距：2.54 cm
左边距：3.17 cm（标准）/ 1.91 cm（短篇）
右边距：3.17 cm（标准）/ 1.91 cm（短篇）
```

### 1.3 字体层级

| 层级            | 字体           | 字号            | 字重   | 对齐   | 行距         |
|-----------------|----------------|-----------------|--------|--------|--------------|
| 中文标题        | 华文中宋       | 18pt            | Bold   | 居中   | 固定值 17pt  |
| 英文标题        | Times New Roman| 14pt            | Normal | 居中   | 固定值 17pt  |
| 摘要/正文       | 宋体           | 10.5pt (5号)    | Normal | 两端对齐 | 固定值 17pt |
| 一级章节标题    | 宋体           | 12pt            | Bold   | 左对齐缩进24pt | 固定值 17pt |
| 二级章节标题    | 宋体           | 10.5pt          | Bold   | 左对齐缩进21pt | 固定值 17pt |
| 英文/数字       | Times New Roman| 10.5pt          | Normal | 行内嵌入 | 固定值 17pt  |
| 图注            | 宋体           | —               | Normal | 居中缩进0pt | 固定值 17pt |
| 参考文献        | Times New Roman| —               | Normal | 左对齐缩进0pt | 固定值 17pt |

### 1.4 段落格式

| 类型           | 首行缩进 | 段前距 | 段后距 |
|----------------|----------|--------|--------|
| 正文段落       | 21pt     | 4pt    | 0pt    |
| 章节标题       | 24pt     | 7.8pt  | 7.8pt  |
| 图注/参考文献  | 0pt      | 4pt    | 0pt    |

### 1.5 结构模板

```
论文标题（华文中宋 18pt）
英文标题（Times New Roman 14pt）

摘要：xxx（宋体 10.5pt）
关键词：xxx；xxx；xxx

Abstract: xxx
Keywords: xxx

0/1 引言
  正文段落（宋体 10.5pt，首行缩进21pt，行距固定17pt）
  1.1 子标题（宋体 10.5pt Bold，缩进21pt）
    正文段落...
    图[1] 图注内容. 来源[序号]

2 章节标题（宋体 12pt Bold）
  2.1 子标题
    ...

X 结语

参考文献
[1] 作者. 标题[D/J]. 出版地：出版社, 年份.
[2] Author. Title[J]. Journal Name, Year.
```

### 1.6 各章节写作规则

#### 引言
- 第一段：交代研究背景，指出核心需求或矛盾
- 第二段：描述技术/方法发展现状，用引用佐证  
- 第三段：明确本文研究目标、方法和结构概述
- 涉及跨学科时，诚实地说明自己的学科背景和局限
- 引言通常包含 3-6 个引用

#### 主体章节
- 每节写一个技术维度或分析维度的内容
- 每节内部：首段总述 → 子节逐项展开
- 每个子节至少：定义/原理 → 优势 → 局限/问题 → (示例/引用)
- 引用应编织进句子中："XX研究指出..."，而非独立括号
- 图/表格式：图[序号] 图注内容 作者. 来源
- 英文专业术语在中文正文中保留英文原文

#### 结语
- 总结主要发现和结论
- 指出研究意义和贡献
- 客观列出局限
- 展望未来方向
- 语气学术、客观，不使用文学修辞

### 1.7 参考文献规范

```
中文书籍：  [序号] 作者. 书名[M]. 出版地：出版社, 年份.
中文期刊：  [序号] 作者. 文章名[J]. 期刊名, 年份(期号): 页码.
学位论文：  [序号] 作者. 论文名[D]. 出版地：大学名, 年份.
英文文献：  [序号] Author. Title[J/Book]. Publisher, Year.
网页来源：  [序号] 标题[EB/OL]. URL, 访问日期.

🔴 铁律：不得虚构任何参考文献
🔴 铁律：不确定的引用用 [待补充] 标记，让用户确认
🔴 铁律：英文术语必须使用 Times New Roman 字体
```

### 1.8 输出

Generate a formatted .docx file using python-docx.

```
输出文件：[论文名]_by_LeoLee.docx
- 页面设置：L/R 3.17cm, T/B 2.54cm
- 正文：宋体 10.5pt, 行距固定 17pt
- 首行缩进 21pt
- 章节编号自动生成
```

---

## [2] 演讲稿写作模块

### 2.1 收集需求

When entering speech mode, ask:

1. 场合：开题答辩 / 期末汇报 / 学术会议
2. 是否已有 .pptx 文件？(Y/N) — 如果有，提供路径
3. 演讲时长（分钟）
4. 听众背景
5. 语言：中文 / 英文
6. 输出目录

### 2.2 10 步工作流

```
Step 1: 读取 .pptx → 提取文字/表格/图表结构
        python scripts/read_slides.py <deck.pptx> --output <output-dir>/work/slide_extract.json

Step 2: 渲染每页为 PNG 图像
        python scripts/render_slides.py <deck.pptx> --output-dir <output-dir>/work/rendered_slides

Step 3: 构建可见元素清单
        python scripts/visual_inventory.py --extract <extract.json> --rendered-dir <rendered/> --output <work/visual_inventory.json>

Step 4: 视觉审查（图表/图片/表格）
        python scripts/vision_review.py --inventory <inventory.json> --output <work/vision_review_packet.json>

Step 5: 生成讲稿理解摘要（论点、结构、关键参数）

Step 6: 收集上下文（时长、听众、场合、语言）

Step 7: 确认叙事弧线（开篇入题、中段转折、结尾收束）

Step 8: 逐页撰写讲稿
        - 每页以核心论点开头
        - 禁止 "This slide shows..." / "这一页展示了..."
        - 先陈述结论/观点，再解释论据

Step 9: 注入 PPTX 备注栏
        python scripts/inject_notes.py <deck.pptx> --notes <notes.json> --output <deck>-with-notes.pptx

Step 10: 输出排练文档
         python scripts/write_display_docx.py --notes <notes.json> --output <deck>-display.docx
```

### 2.3 输出

```
<演讲名>-speaker-output/
├── <演讲名>-with-notes.pptx    ← 带备注的 PPT
├── <演讲名>-display.docx       ← 排练文稿
└── work/                       ← 中间处理文件（不展示给用户）
```

---

## Scripts

This skill includes Python scripts from the speaker skill (AI272/speaker) for PPT speech writing:

- `scripts/read_slides.py`     — Extract structured slide content from .pptx
- `scripts/render_slides.py`   — Render slides to PNG images
- `scripts/visual_inventory.py` — Build visible-element inventory
- `scripts/vision_review.py`   — Run vision-capable review on slides
- `scripts/inject_notes.py`    — Inject speaker notes into .pptx notes pane
- `scripts/write_display_docx.py` — Generate display rehearsal document

For paper writing, use python-docx to generate formatted .docx output.
