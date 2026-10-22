<!-- Hero -->
<div align="center">
  <h1>学习项目模板</h1>
  <p><b>放在你自己电脑上的 Claude Project</b>：每个科目一个文件夹，里面放你的教材、笔记和 AI 的记忆，所以你在那里打开的任何 agent 都能从上一个停下的地方接着教。</p>
  <p>
    <img alt="agents: Claude Code | OpenCode | DeepSeek Harness" src="https://img.shields.io/badge/agents-Claude%20Code%20%7C%20OpenCode%20%7C%20DeepSeek%20Harness-4d6bfe">
    <img alt="content: Markdown only" src="https://img.shields.io/badge/content-Markdown%20only-brightgreen">
  </p>
  <p>🌏 简体中文 · <a href="./README.zh-TW.md">繁體中文</a> · <a href="./README.md">English</a></p>
</div>

<!-- Screenshot placeholder: commit the image at docs/screenshot.png, then remove this comment pair.
<p align="center"><img src="docs/screenshot.png" alt="VS Code 里黑板上的一堂课" width="720"></p>
-->

假设上课上到一半 Claude 的额度用完，你换了另一个 agent。平常新的 agent 什么都不知道，你得从头解释一遍。在这里，记忆是文件夹里的普通文件，每个 agent 读写的都是同一批文件，而且边做边存：一个 agent 突然停掉，最多只会损失最后几分钟。

## ✨ 功能

- **记忆就是普通文件**：你学到哪、懂了什么、做过什么决定、接下来做什么，都在 `memory/` 里。
- **随时换 agent**：关掉一个，在同一个文件夹打开另一个，它会告诉你学到哪里。
- **边做边存**：不用特别让它存；只有想一次全部存好时才说“handoff”。
- **黑板**：教学内容写在 `materials/generated/blackboard.md`，VS Code 会直接显示排版好的样子，数学式也是；聊天只留简短消息。
- **用你的语言**：写给你看的都用你选的语言；写给 AI 的保持英文。
- **模式**：说“我三天后考试”或“今天只想练习”，教法就会跟着变。
- **迁移 Claude Project**：你的指示、教材和进度都能一起带过来。

## 🚀 安装

前提：git、VS Code，以及至少一个 agent：Claude Code、OpenCode 或 DeepSeek Harness。

**方式一 · Windows（PowerShell）**

```powershell
git clone https://github.com/ctyson0606/LearningProject.git
mkdir D:\learning\my-topic
Copy-Item -Recurse LearningProject\template\* D:\learning\my-topic\
```

**方式二 · macOS 或 Linux**

<details>
<summary>同样的步骤，用 POSIX shell</summary>

```bash
git clone https://github.com/ctyson0606/LearningProject.git
mkdir -p ~/learning/my-topic
cp -r LearningProject/template/. ~/learning/my-topic/
```

</details>

新文件夹要建在这个仓库**外面**，然后把你的书、幻灯片和往年试题放进它的 `materials/sources/`。

**验证**

用 VS Code 打开新文件夹，在里面启动一个 agent，随便说句话，例如“hi”。它会先问你想用哪种语言。

## 🕹️ 使用

### 第一次对话

1. agent 会问你的语言，再问这是新科目，还是从 Claude Project 迁移过来的。
2. 如果是新科目，它会问几个关于你的目标和学习习惯的问题。
3. 它会给你看一份简短的教学方式摘要。你说没问题之后，就开始上课。

### 迁移现有的 Claude Project

照上面安装，然后选“从 Claude Project 迁移过来”。agent 会请你：

- 把旧的项目指示给它，粘贴或提供文件都可以；
- 把原始教材放进 `materials/sources/`，之前 AI 帮你做的东西放进 `materials/generated/`；
- 问旧的 Claude Project“我们学到哪里了，接下来做什么？”，再把回答粘贴过来。

它会把你的指示翻译成英文，改掉只在 claude.ai 上才有用的部分，保存前把每一处改动都给你看。

### 换到另一个 agent

关掉旧的 agent，在同一个文件夹打开新的。如果旧的还能用，先说“handoff”。同一时间一个文件夹只开一个 agent：如果看起来还有别的 session 开着，新的会先问你再继续。

### 你可以说的话

| 说 | 会发生什么 |
| --- | --- |
| “我三天后考试” | 冲刺：只教考试需要的，大量练习 |
| “今天只想练习” | 练习：不教新东西，只做题和订正 |
| “回到正常” | 恢复正常教学 |
| “Handoff” | 立刻存好一切，方便你换 agent |
| “我加了新文件” | 它会读那些文件，并更新你的教材清单 |

如果你的项目指示定义了自己的模式，就以那些为准。

## 📁 你的文件夹里有什么

| 路径 | 是什么 | 谁写 |
| --- | --- | --- |
| `AGENTS.md` | 每个 agent 都要遵守的规则，以及这个项目怎么教你 | 设置时由 agent 写；之后只在你要求时才改 |
| `CLAUDE.md` | 让 Claude Code 去读 `AGENTS.md` | 没人写；保持原样 |
| `materials/sources/` | 你的原始教材 | 你；agent 只会读 |
| `materials/generated/` | agent 帮你做的东西：笔记、练习、摘要 | agent |
| `materials/generated/blackboard.md` | 当前的教学内容，数学式正确显示 | agent |
| `materials/generated/obsidian/` | 可以用 Obsidian vault 打开的笔记 | agent |
| `memory/` | 你学到哪、懂了什么、决定、待办、每次 session 的摘要 | agent，自动 |

## 📊 状态

已经在六个真实科目的文件夹里天天使用，主要用 Claude Code。2026-10-21 在其中一个的副本上，分别用 Claude Code、OpenCode 和 DeepSeek Harness 跑了同样的两轮对话：

- **交接可行**：一个 OpenCode session 没有 handoff 就关掉，在同一个文件夹打开 Claude Code，它说出了学习进度。
- **模型比 agent 更重要**：用 DeepSeek V4.1 Flash 时，OpenCode 和 DeepSeek Harness 都遵守了每条规则；免费和本地模型只适合短暂接手。
- **还没试过**：OpenCode 和 DeepSeek Harness 的交互界面，这次都是一次一个命令驱动的。

## 📦 项目结构

```text
template/AGENTS.md
template/CLAUDE.md
template/materials/sources/
template/materials/generated/blackboard.md
template/memory/
template/.vscode/settings.json
```

- `template/AGENTS.md`：每个复制出来的文件夹一开始带着的规则和教学方法；
- `template/CLAUDE.md`：Claude Code 会读的指引；
- `template/materials/sources/`：空的，放学习者的教材；
- `template/materials/generated/blackboard.md`：黑板；
- `template/memory/`：记忆文件，保持初始格式；
- `template/.vscode/settings.json`：把黑板以排版预览打开，并启用数学式。

只有 `template/` 会被复制。这个仓库的其他部分（`kit/`、`scripts/`、最上层的 `AGENTS.md`）是用来制作模板的工具。

## ⚠️ 兼容性与限制

- Claude Code 能读 `materials/sources/` 里的 PDF；OpenCode 和 DeepSeek Harness 能不能读还不知道。
- DeepSeek Harness 最多只加载 64 KiB 的指示，所以 `AGENTS.md` 超过 60,000 bytes 时，agent 会建议把一部分移到 `memory/`。
- 如果有东西（同步、git 操作）改动了所有文件的日期，即使没有别的 session 开着，打开 session 时的检查也可能会问你。
- 日期一律用英国日期，也不写时刻，不管 agent 在哪台电脑上运行。

## ❓ 常见问题

| 症状 | 怎么做 |
| --- | --- |
| 上课上到一半 Claude 额度用完 | 在同一个文件夹打开另一个 agent；它会从记忆接着教 |
| 新的 agent 问是不是还有别的 session 开着 | 把另一个关掉，或告诉它已经关了 |
| 数学式在聊天里显示成原始 LaTeX | 看黑板；VS Code 会排版显示 |
| 命令行的 DeepSeek Harness 读不到你的 API key | 在环境变量设置 `DEEPSEEK_API_KEY`；网页设置里存的 key 在那里不会被用到 |
