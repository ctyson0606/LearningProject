# Learning Project Template

English | [繁體中文](README.zh-TW.md) | [简体中文](README.zh-CN.md)

A folder template that works like a Claude Project, but on your own computer.

Every time you want to learn something new, you copy this template into a new
folder. That folder keeps your material, your notes, and the AI's memory of
where you are. Any AI agent you open in it, such as Claude Code, OpenCode or
DeepSeek Harness, reads that memory first. So it knows what you have learned,
what you talked about last time, and what comes next.

## Why

Say Claude runs out of quota halfway through a lesson and you switch to
another agent. Normally the new agent knows nothing, and you have to explain
everything again.

Here, the memory is plain files inside the folder, and every agent reads and
writes the same files. The agent saves as it goes, so even if it stops
suddenly, you lose at most the last few minutes.

## Start a new subject

1. Download this repository:

```
git clone https://github.com/ctyson0606/LearningProject.git
```

2. Make a new folder **outside** this repository, and copy everything inside
   `template/` into it. On Windows (PowerShell):

```
mkdir D:\learning\my-topic
Copy-Item -Recurse LearningProject\template\* D:\learning\my-topic\
```

   On macOS or Linux:

```
mkdir -p ~/learning/my-topic
cp -r LearningProject/template/. ~/learning/my-topic/
```

3. Put your material (books, slides, past papers) into `materials/sources/`.
4. Open the new folder in VS Code, start an agent there, and say anything,
   for example "hi".
5. It asks which language you want, then whether this is a new subject or one
   you are moving from a Claude Project. Choose new, and answer a few
   questions about your goal and how you like to learn.
6. It shows you a short summary of how it will teach you. Once you say it is
   fine, you can start learning.

## Move an existing Claude Project

Do steps 1 to 4 above, then choose "moving from a Claude Project". The agent
will ask you to:

- give it your old project instructions (paste them, or tell it where the
  file is);
- put your original material into `materials/sources/`, and anything an AI
  made for you before (notes, error logs) into `materials/generated/`;
- ask your old Claude Project "where are we, and what's next?", and paste the
  answer.

It translates your instructions into English, changes the parts that only
work on claude.ai, and shows you every change before it saves anything.

## Switch to another agent

Close the old agent and open the new one in the same folder. That is all. The
new agent tells you where you are as soon as it starts.

If the old agent still works, you can say "handoff" first, so it saves the
last few minutes.

## Things you can say

| Say | What happens |
|---|---|
| "My exam is in 3 days" | Sprint: only what the exam needs, lots of exercises |
| "Just practice today" | Practice: nothing new, only exercises and corrections |
| "Back to normal" | Normal teaching again |
| "Handoff" | Saves everything right now, before you switch |
| "I added new files" | It reads them and updates its list of your material |

If your project instructions define their own modes, those are used instead.

## What is in the folder

| Path | What it is | Who writes it |
|---|---|---|
| `AGENTS.md` | Rules every agent follows, and how this project teaches you | The agent during setup; later only when you ask |
| `CLAUDE.md` | Points Claude Code to `AGENTS.md` | Nobody; leave it as it is |
| `materials/sources/` | Your original material | You. Agents only read it |
| `materials/generated/` | Things the agent makes for you: notes, exercises, summaries | The agent |
| `materials/generated/blackboard.md` | The blackboard: the current teaching, with math shown properly | The agent |
| `materials/generated/obsidian/` | Notes you can open as an Obsidian vault | The agent |
| `memory/` | Where you are, what you know, decisions, to-dos, conversation summaries | The agent, automatically |

The agent teaches on the blackboard and keeps the chat for short messages,
because the chat window cannot show math formulas and long explanations
scroll away. In VS Code the blackboard opens already rendered.

Files meant for the AI (`AGENTS.md` and `memory/`) are in English. Everything
meant for you is in the language you chose.

## Status

This is an early version and has not been fully tested. Setting up a project
and switching between agents have not yet been tried with real agents.

The rest of this repository (`kit/`, `scripts/`, the top-level `AGENTS.md` and
so on) is the tooling used to build the template. To use the template, you
only need the `template/` folder.
