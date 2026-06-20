# leolee-writing — Codex Writing Skill

基于 LeoLee 实际论文和演讲稿分析提炼的个人写作规范 skill。

## 功能

- **📄 论文写作** — 遵循 LeoLee 个人格式规范（宋体 10.5pt、行距固定 17pt、页边距 3.17cm 等）生成 .docx
- **🎤 演讲稿写作** — 整合 speaker 工作流，基于 .pptx 逐页撰写注备讲稿

## 多轮对话工作流

### 论文 (5 轮)
1. **主题与范围** — 明确题目、角度、类型、字数
2. **文献检索** — 搜索真实文献并由用户确认
3. **大纲生成** — 生成章节结构并由用户确认
4. **逐节确认** — 逐节讨论内容要点
5. **生成与审阅** — 输出格式化的 .docx

### 演讲 (4 轮)
1. **情境收集** — 场合、时长、语言
2. **叙事弧线** — 确认开篇/中段/结尾方向
3. **幻灯片审阅** — 读取 .pptx 内容并呈现
4. **生成与注入** — 写入 PPTX 备注栏

## 格式规范

| 层级 | 字体 | 字号 | 行距 |
|------|------|------|------|
| 中文标题 | 华文中宋 | 18pt Bold | 固定 17pt |
| 英文标题 | Times New Roman | 14pt | 固定 17pt |
| 正文 | 宋体 | 10.5pt (5号) | 固定 17pt |
| 一级章节标题 | 宋体 | 12pt Bold | 固定 17pt |
| 英文/数字 | Times New Roman | 10.5pt | 行内嵌入 |

## 参考文献规则

- 所有引用必须真实可查，不得虚构
- 不确定的用 [待补充] 标记

## 安装

```bash
python install-skill-from-github.py --url https://github.com/everglowwwww/LeoLee-Artical-and-Speech/tree/main/skill/leolee-writing
```

重启 Codex 后即可用。
