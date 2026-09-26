# 学习项目模板

[English](README.md) | [繁體中文](README.zh-TW.md) | 简体中文

一个文件夹模板，用起来就像 Claude Project，只是放在你自己的电脑上。

每次想学新东西，就把这个模板复制到一个新文件夹。这个文件夹会保存你的资料、你的笔记，以及 AI 对你学习进度的记忆。你在里面打开任何一个 AI Agent，例如 Claude Code、OpenCode 或 DeepSeek Harness，它都会先读这份记忆。所以它知道你学了什么、上次聊了什么、下一步要做什么。

## 为什么需要它

假设上课上到一半，Claude 的额度用完了，你换成另一个 Agent。一般情况下，新的 Agent 什么都不知道，你得从头再解释一遍。

在这里，记忆就是文件夹里的普通文件，每个 Agent 都读写同一份文件。Agent 会边学边存，所以就算它突然停掉，你最多只会少掉最后几分钟。

## 开始学一个新主题

1. 下载这个 repository：

```
git clone <repository-url>
```

2. 在这个 repository **外面**新建一个文件夹，把 `template/` 里面的所有东西复制进去。Windows（PowerShell）：

```
mkdir D:\learning\my-topic
Copy-Item -Recurse LearningProject\template\* D:\learning\my-topic\
```

   macOS 或 Linux：

```
mkdir -p ~/learning/my-topic
cp -r LearningProject/template/. ~/learning/my-topic/
```

3. 把你的资料（课本、幻灯片、历年真题）放进 `materials/sources/`。
4. 在新文件夹里打开一个 Agent，随便说一句话，例如「hi」。
5. 它会先问你要用什么语言，再问这是新主题，还是从 Claude Project 搬过来的。选「新主题」，然后回答几个关于你的目标、你喜欢怎么学的问题。
6. 它会给你看一份简短的摘要，说明它打算怎么教你。你说没问题之后，就可以开始学了。

## 迁移现有的 Claude Project

先做完上面的第 1 到第 4 步，然后选「从 Claude Project 搬过来」。Agent 会请你：

- 把旧的项目指令给它（直接粘贴，或告诉它文件放在哪里）；
- 把原始资料放进 `materials/sources/`，把以前 AI 帮你做的东西（笔记、错题本）放进 `materials/generated/`；
- 去问你旧的 Claude Project「我们学到哪里了？下一步是什么？」，然后把回答粘贴给它。

它会把你的指令翻译成英文，改掉只在 claude.ai 上才能用的部分，并在保存之前，把每一处改动都给你看过。

## 换到另一个 Agent

关掉旧的 Agent，在同一个文件夹打开新的 Agent，这样就好了。新的 Agent 一启动就会告诉你目前学到哪里。

如果旧的 Agent 还能用，可以先说一声「交接」，让它把最后几分钟也存起来。

## 你可以这样说

| 你说 | 会发生什么 |
|---|---|
| 「我 3 天后要考试」 | 冲刺：只学考试需要的，大量做题 |
| 「今天只想练习」 | 练习：不教新东西，只出题和订正 |
| 「回到平常」 | 回到一般的教学方式 |
| 「交接」 | 马上把所有东西存起来，方便你换 Agent |
| 「我加了新文件」 | 它会读新文件，并更新资料清单 |

如果你的项目指令有自己定义的模式，就改用那些模式。

## 文件夹里有什么

| 路径 | 是什么 | 谁来写 |
|---|---|---|
| `AGENTS.md` | 每个 Agent 都要遵守的规则，以及这个项目要怎么教你 | 设置时由 Agent 写；之后只在你要求时改 |
| `CLAUDE.md` | 让 Claude Code 去读 `AGENTS.md` | 不用动它 |
| `materials/sources/` | 你的原始资料 | 你。Agent 只会读 |
| `materials/generated/` | Agent 帮你做的东西：笔记、练习题、摘要 | Agent |
| `materials/generated/obsidian/` | 可以直接用 Obsidian 打开的笔记 | Agent |
| `memory/` | 学到哪里、你懂什么、做过的决定、待办、对话摘要 | Agent，自动更新 |

给 AI 看的文件（`AGENTS.md` 和 `memory/`）用英文。给你看的东西，都用你选的语言。

## 目前状态

这是早期版本，还没有完整测试过。创建项目、在不同 Agent 之间切换，都还没有用真的 Agent 实际跑过。

这个 repository 里的其他东西（`kit/`、`scripts/`、最外层的 `AGENTS.md` 等等）是用来开发这个模板的工具。要使用模板，你只需要 `template/` 这个文件夹。
