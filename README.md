# LeoLee Artical and Speech

个人学术写作与演讲的 Codex Skill 工具集。

## 目录结构

```
├── skill/leolee-writing/          ← Codex 可安装的全局 skill
│   ├── SKILL.md                   ← skill 指令（论文+演讲规范 + 多轮工作流）
│   ├── README.md                  ← 安装与使用说明
│   └── scripts/                   ← 演讲稿生成辅助脚本
│       ├── read_slides.py         ← 读取 .pptx 内容
│       ├── render_slides.py       ← 渲染 PPT 为 PNG
│       ├── visual_inventory.py    ← 构建可见元素清单
│       ├── vision_review.py       ← 视觉审查
│       ├── inject_notes.py        ← 注入备注到 PPTX
│       └── write_display_docx.py  ← 生成排练文稿
└── README.md                      ← 本文件
```

## leolee-writing 是什么

基于 LeoLee 实际撰写的多篇论文和演讲稿，提炼出的个人写作规范 skill。覆盖格式、结构、语言风格、参考文献准则，并通过**多轮对话工作流**确保产出质量。

包含两大功能模块：

| 模块 | 说明 |
|------|------|
| 📄 **论文写作** | 按 LeoLee 的个人格式规范生成 .docx 论文 |
| 🎤 **演讲稿写作** | 基于 .pptx 逐页撰写学术演讲稿 |

## 论文写作 — 5 轮对话工作流

```
Round 1 │ 主题与范围 → 明确题目、角度、类型、字数、格式
Round 2 │ 文献检索   → 联网搜索真实文献 → 用户确认
Round 3 │ 大纲生成   → 生成章节结构 → 用户确认
Round 4 │ 逐节确认   → 每节讨论内容要点 → 用户确认
Round 5 │ 生成 & 审阅 → 输出 .docx → 用户修改
```

## 演讲稿写作 — 4 轮对话工作流

```
Round 1 │ 情境收集     → 场合、时长、语言、是否提供 .pptx
Round 2 │ 叙事弧线     → 开篇/中段/结尾方向确认
Round 3 │ 幻灯片审阅   → 读取 .pptx 内容呈现给用户
Round 4 │ 生成 & 注入   → 写入 PPTX 备注栏或生成 .docx
```

## 格式规范

| 参数 | 标准值 |
|------|--------|
| 正文 | 宋体 10.5pt (5号)，行距固定 17pt |
| 英文/数字 | Times New Roman 10.5pt |
| 标题 | 华文中宋 18pt |
| 章节标题 | 宋体 12pt（一级）/ 10.5pt（二级） |
| 页边距 | L/R 3.17cm，T/B 2.54cm |
| 首行缩进 | 21pt（约2个汉字） |

## 参考文献铁律

- 🔴 **不得虚构参考文献**，所有引用必须真实可查
- 🔴 不确定的引用留 **[待补充]** 标记
- 🔴 省略的引用由用户确认后再补充

## 安装

### 方式一：Codex 自动安装

```bash
python install-skill-from-github.py --url https://github.com/everglowwwww/LeoLee-Artical-and-Speech/tree/main/skill/leolee-writing
```

### 方式二：手动复制

```bash
cp -r skill/leolee-writing ~/.codex/skills/leolee-writing
```

重启 Codex 后即可使用。

## 使用方式

| 你说 | 效果 |
|------|------|
| "用 leolee-writing 写论文" | 启动 5 轮论文写作工作流 |
| "用 leolee-writing 写演讲稿" | 启动 4 轮演讲稿写作工作流 |
| "帮我写一篇关于 XX 的课程论文" | 自动路由到论文写作模式 |

---

*基于真实写作数据分析生成。*
