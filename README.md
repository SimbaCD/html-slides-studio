# HTML Slides Studio

`html-slides-studio` 是一个 Codex Skill，用来把一份较详细的演讲大纲、文稿或主题材料，转成高审美、可编辑、可导出的单文件 HTML 演示文稿。  
`html-slides-studio` is a Codex skill for turning a detailed outline, manuscript, or topic brief into a high-aesthetic, editable, exportable single-file HTML slide deck.

这个公开仓库保存的是 **适合公开分享的净化版本**。  
This public repository contains the **sanitized public version** of the skill.

仓库里的模板全部使用占位内容，不包含私人稿件、真实客户材料、二维码或个人联系信息。  
All templates in this repository use placeholder content and do not include private manuscripts, client materials, QR codes, or personal contact information.

## 这是什么 / What This Is

这个 Skill 不是一个“直接乱生成整场演讲”的工具。  
This skill is not meant to blindly invent an entire talk from scratch.

它的核心用途是：  
Its core purpose is:

1. 先接收你已经有的内容框架  
   Start from material you already have
2. 先规划页纲，再生成页面  
   Plan the slide list first, then generate slides
3. 用更适合 AI 编辑的 HTML，而不是传统 PPT  
   Use AI-friendly HTML instead of traditional PPT
4. 交付一个可继续编辑、可导出 PDF 的演示文稿  
   Deliver a deck that remains editable and can be exported to PDF

它适合这些场景：  
It is useful for:

- 课程培训  
  Training sessions
- 主题演讲  
  Talks and keynote-style presentations
- 高审美展示页  
  High-aesthetic presentation decks
- 需要交互、动画或演讲者视图的 slides  
  Slides that need interaction, animation, or presenter view

## 核心工作流 / Core Workflow

这个 Skill 会强制采用更稳定的工作流，而不是直接开始写代码。  
The skill enforces a more reliable workflow instead of jumping straight into code.

1. 先选择设计风格  
   Choose a design language first
2. 补齐输入信息  
   Fill in the missing talk inputs
3. 先规划完整页纲  
   Plan the full page list first
4. 等用户确认  
   Wait for user confirmation
5. 再生成或修改最终 HTML  
   Then generate or revise the final HTML deck

这比“先出代码再慢慢返工”更稳定。  
This is much more reliable than generating code first and fixing structure later.

## 四套设计语言 / Four Design Languages

Skill 自带四套视觉系统：  
The skill ships with four visual systems:

1. `A · Warm Editorial / 暖纸编辑`
2. `B · Dark Terminal / 深空终端`
3. `C · Swiss Grid / 包豪斯网格`
4. `D · Japanese Ink / 日式墨稿`

模板文件位于：  
Template files are located in:

- `assets/template-a-warm-editorial.html`
- `assets/template-b-terminal.html`
- `assets/template-c-swiss.html`
- `assets/template-d-ink.html`

## 功能概览 / Feature Overview

目前这个 Skill 的公开版能力包括：  
The public version of the skill currently includes:

- 单文件 HTML 输出  
  Single-file HTML output
- 16:9 演讲比例  
  16:9 presentation layout
- 先页纲确认，再生成代码  
  Page-plan confirmation before code generation
- 演讲者视图 / speaker notes  
  Presenter view / speaker notes
- 前端编辑模式  
  Front-end edit mode
- 自动保存本地草稿  
  Local autosave for edits
- `Ctrl+S` / `Cmd+S` 保存整份 HTML  
  `Ctrl+S` / `Cmd+S` saves the full HTML document
- 图片插入、拖拽、缩放  
  Image insertion, drag, and resize
- `@media print` 导出逐页 PDF 的基础支持  
  Base support for per-slide PDF export through `@media print`

关于“保存”的实际行为，需要说明清楚：  
The save behavior has one important implementation detail:

- 如果浏览器支持 File System Access API，且用户授权，页面可以直接写回 `.html` 文件  
  If the browser supports the File System Access API and the user grants permission, the page can write back directly to the `.html` file
- 如果浏览器不支持，或者当前环境无法直接写回，就会退化为下载一份完整更新后的 HTML 文件  
  If direct write-back is unavailable, it falls back to downloading a fully updated HTML file

## 仓库结构 / Repository Structure

```text
.
├─ SKILL.md
├─ README.md
├─ agents/
│  └─ openai.yaml
├─ assets/
│  ├─ slides-template-v3.html
│  ├─ template-a-warm-editorial.html
│  ├─ template-b-terminal.html
│  ├─ template-c-swiss.html
│  └─ template-d-ink.html
├─ references/
│  ├─ content-playbook.md
│  ├─ design-rules.md
│  └─ implementation-rules.md
└─ scripts/
   └─ new_slides.ps1
```

简要说明：  
Quick explanation:

- `SKILL.md`：给 Codex 看的主技能说明  
  `SKILL.md`: the main machine-facing instruction file for Codex
- `README.md`：给人看的仓库介绍  
  `README.md`: the human-facing repository introduction
- `assets/`：模板资产  
  `assets/`: template assets
- `references/`：规则、流程、设计语言说明  
  `references/`: rules, workflow notes, and design-language references
- `scripts/`：辅助脚本  
  `scripts/`: helper scripts

## 安装方式 / Installation

如果你使用 Codex 本地技能目录，可以把这个文件夹复制进去。  
If you use local Codex skills, copy this folder into your Codex skills directory.

Windows 常见路径：  
Typical path on Windows:

```text
C:\Users\<your-user>\.codex\skills\html-slides-studio
```

macOS / Linux 常见路径：  
Typical path on macOS / Linux:

```text
~/.codex/skills/html-slides-studio
```

安装后，在对话中可以这样触发：  
After installation, trigger it like this:

```text
Use $html-slides-studio ...
```

## 怎么使用 / How To Use

这个 Skill 最适合的输入，不是一句空泛主题，而是这些信息：  
This skill works best when the input is not just a vague topic, but includes:

- 演讲标题  
  A talk title
- 听众画像  
  Audience profile
- 时长  
  Duration
- 比较详细的大纲  
  A reasonably detailed outline
- 特殊要求  
  Special requirements

一个最小可用示例如下：  
A minimal workable example looks like this:

```text
风格选择：A
演讲标题：你的标题
副标题/关键词：可空
演讲者：你的名字 / 机构 / 日期
时长：45 分钟
听众：律师 / 程序员 / 投资人 / 大众

大纲：
Part 1 - 问题
  1.1 旧流程的摩擦
  1.2 为什么是现在
Part 2 - 方法
  2.1 工作流
  2.2 演示
Part 3 - 行动
  3.1 风险
  3.2 下一步

特殊要求：
- 需要截图
- 需要讲稿提示
- 需要 PDF 导出兼容
```

你也可以这样直接发 prompt：  
You can also trigger it with prompts like:

```text
Use $html-slides-studio to turn my detailed outline into a single-file HTML slide deck.
```

```text
Use $html-slides-studio. Start by asking me to choose A/B/C/D, then help me plan the deck before writing code.
```

```text
Use $html-slides-studio to revise this existing HTML deck, keep the interaction quality high, and add edit/save behavior.
```

## 为什么是 HTML 而不是 PPT / Why HTML Instead Of PPT

这个 Skill 的出发点不是“为了炫技”，而是因为 HTML 更适合 AI 和人一起迭代。  
The point of this skill is not novelty for its own sake, but the fact that HTML is easier for both AI and humans to iterate on.

原因包括：  
Reasons include:

- HTML/CSS/JS 是纯文本，AI 更容易局部修改  
  HTML/CSS/JS is plain text, so AI can modify it more precisely
- 前端交互和动画比传统 PPT 更自由  
  Front-end interaction and animation are more flexible than traditional PPT
- 可以把“展示”和“编辑”放在同一个页面里  
  Presentation and editing can coexist in the same page
- 更容易做版本管理和复用模板  
  Versioning and template reuse are easier

## 公开版边界 / Public-Safe Boundary

这个仓库是公开分享版，因此做了明确裁剪：  
This repository is the public-safe version, so it has been deliberately trimmed.

- 使用占位内容，不放真实课程稿件  
  Placeholder content only, no real course manuscripts
- 不放个人二维码  
  No personal QR codes
- 不放真实客户资料  
  No client materials
- 不放你的私人联系信息  
  No private contact details
- 不放你之前做过的真实课件原文  
  No verbatim reuse of your previous real decks

如果你要做自己的正式版本，建议在本地安装后自行替换内容。  
If you want to build your real production version, install the skill locally and replace the placeholders there.

## 适合谁 / Who This Is For

这个仓库尤其适合：  
This repository is especially useful for:

- 想用 HTML 代替 PPT 的内容创作者  
  Content creators who want HTML instead of PPT
- 需要高审美课件的人  
  People who care about presentation aesthetics
- 想把大纲稳定转成演示稿的人  
  People who want a reliable outline-to-deck workflow
- 想做“先页纲确认，再生成代码”流程的人  
  People who want a page-planning-first workflow

## License

当前仓库默认没有附带单独的 license 文件。  
This repository currently does not include a separate license file by default.

如果你希望别人明确知道是否可以复用、修改或商用，建议补一个 `LICENSE`。  
If you want others to clearly know whether reuse, modification, or commercial use is allowed, add a `LICENSE` file.
