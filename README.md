<!-- Hero -->
<div align="center">
  <h1>Learning Project Template</h1>
  <p><b>A Claude Project on your own computer</b>: one folder per subject holds your material, your notes and the AI's memory, so any agent you open there picks up where the last one stopped.</p>
  <p>
    <img alt="agents: Claude Code | OpenCode | DeepSeek Harness" src="https://img.shields.io/badge/agents-Claude%20Code%20%7C%20OpenCode%20%7C%20DeepSeek%20Harness-4d6bfe">
    <img alt="content: Markdown only" src="https://img.shields.io/badge/content-Markdown%20only-brightgreen">
  </p>
  <p>🌏 <a href="./README.zh-CN.md">简体中文</a> · <a href="./README.zh-TW.md">繁體中文</a> · English</p>
</div>

<!-- Screenshot placeholder: commit the image at docs/screenshot.png, then remove this comment pair.
<p align="center"><img src="docs/screenshot.png" alt="A lesson on the blackboard in VS Code" width="720"></p>
-->

Say Claude runs out of quota halfway through a lesson and you switch to another agent. Normally the new one knows nothing and you explain everything again. Here the memory is plain files inside the folder, every agent reads and writes the same files, and they save as they go: an agent that stops suddenly loses at most the last few minutes.

## ✨ Features

- **Memory in plain files**: where you are, what you know, what was decided and what comes next, in `memory/`.
- **Switch agents any time**: close one, open another in the same folder, and it tells you where you are.
- **Saves as it goes**: no need to ask; say "handoff" only when you want everything saved at once.
- **A blackboard**: the teaching goes on `materials/generated/blackboard.md`, which VS Code opens rendered, math included; the chat keeps to short messages.
- **Your language**: everything meant for you is in the language you choose; what is meant for the AI stays in English.
- **Modes**: say "my exam is in 3 days" or "just practice today", and the teaching changes.
- **Move a Claude Project**: your instructions, material and progress come with you.

## 🚀 Installation

Prerequisite: git, VS Code, and at least one agent: Claude Code, OpenCode or DeepSeek Harness.

**Option 1 · Windows (PowerShell)**

```powershell
git clone https://github.com/ctyson0606/LearningProject.git
mkdir D:\learning\my-topic
Copy-Item -Recurse LearningProject\template\* D:\learning\my-topic\
```

**Option 2 · macOS or Linux**

<details>
<summary>The same, in a POSIX shell</summary>

```bash
git clone https://github.com/ctyson0606/LearningProject.git
mkdir -p ~/learning/my-topic
cp -r LearningProject/template/. ~/learning/my-topic/
```

</details>

Make the new folder **outside** this repository, then put your books, slides and past papers into its `materials/sources/`.

**Verify**

Open the new folder in VS Code, start an agent there and say anything, such as "hi". It answers by asking which language you want.

## 🕹️ Usage

### The first conversation

1. The agent asks for your language, then whether this is a new subject or one moving from a Claude Project.
2. For a new subject, it asks a few questions about your goal and how you like to learn.
3. It shows a short summary of how it will teach you. Once you say it is fine, the lessons start.

### Moving an existing Claude Project

Install as above, then choose "moving from a Claude Project". The agent asks you to:

- give it your old project instructions, pasted or as a file;
- put your original material into `materials/sources/`, and anything an AI made for you before into `materials/generated/`;
- ask the old Claude Project "where are we, and what's next?" and paste the answer.

It translates your instructions into English, changes what only works on claude.ai, and shows you every change before saving.

### Switching to another agent

Close the old agent and open the new one in the same folder. If the old one still works, say "handoff" first. Keep one agent per folder at a time: if another session looks open, the new one asks before going on.

### Things you can say

| Say | What happens |
| --- | --- |
| "My exam is in 3 days" | Sprint: only what the exam needs, lots of exercises |
| "Just practice today" | Practice: nothing new, only exercises and corrections |
| "Back to normal" | Normal teaching again |
| "Handoff" | Saves everything now, before you switch |
| "I added new files" | It reads them and updates its list of your material |

If your project instructions define their own modes, those are used instead.

## 📁 What is in your folder

| Path | What it is | Who writes it |
| --- | --- | --- |
| `AGENTS.md` | The rules every agent follows, and how this project teaches you | The agent during setup; later only when you ask |
| `CLAUDE.md` | Points Claude Code to `AGENTS.md` | Nobody; leave it as it is |
| `materials/sources/` | Your original material | You; agents only read it |
| `materials/generated/` | What the agent makes for you: notes, exercises, summaries | The agent |
| `materials/generated/blackboard.md` | The current teaching, with math shown properly | The agent |
| `materials/generated/obsidian/` | Notes you can open as an Obsidian vault | The agent |
| `memory/` | Where you are, what you know, decisions, to-dos, session summaries | The agent, automatically |

## 📊 Status

In daily use across six real subject folders, with Claude Code as the main agent. On 2026-10-21 the same two turns were run in Claude Code, OpenCode and DeepSeek Harness on a copy of one of them:

- **Handover works**: an OpenCode session closed without a handoff, and Claude Code opened in the same folder and stated where the learning stood.
- **The model matters more than the agent**: with DeepSeek V4.1 Flash, OpenCode and DeepSeek Harness both followed every rule; free and local models are fit only for a short pickup.
- **Not yet tried**: the interactive interfaces of OpenCode and DeepSeek Harness, which were driven one shot at a time.

## 📦 Project layout

```text
template/AGENTS.md
template/CLAUDE.md
template/materials/sources/
template/materials/generated/blackboard.md
template/memory/
template/.vscode/settings.json
```

- `template/AGENTS.md`: the rules and the teaching method every copied folder starts with;
- `template/CLAUDE.md`: the pointer Claude Code reads;
- `template/materials/sources/`: empty, for the learner's material;
- `template/materials/generated/blackboard.md`: the blackboard;
- `template/memory/`: the memory files, in their starting shapes;
- `template/.vscode/settings.json`: opens the blackboard as a rendered preview with math on.

Only `template/` is copied. The rest of this repository (`kit/`, `scripts/`, the top-level `AGENTS.md`) is the tooling the template is built with.

## ⚠️ Compatibility and limits

- Claude Code reads PDFs in `materials/sources/`; whether OpenCode and DeepSeek Harness can is not yet known.
- DeepSeek Harness loads at most 64 KiB of instructions, so the agent offers to move part of `AGENTS.md` into `memory/` once it passes 60,000 bytes.
- The open-session check can ask when no other session is open, after something touches every file's date (a sync, a git operation).
- Dates are UK dates and no clock times are written, whichever machine the agent runs on.

## ❓ FAQ

| Symptom | What to do |
| --- | --- |
| Claude ran out of quota mid-lesson | Open another agent in the same folder; it picks up from the memory |
| The new agent asks whether another session is still open | Close the other one, or tell it that it is closed |
| Formulas show as raw LaTeX in the chat | Look at the blackboard; VS Code renders it |
| DeepSeek Harness from the command line does not see your API key | Set `DEEPSEEK_API_KEY` in the environment; a key saved in the web settings is not used there |
