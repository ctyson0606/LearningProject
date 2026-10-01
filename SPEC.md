# SPEC

The contract this project is built against: what the spec gate produced and a
person approved. It stays true for as long as the code does, so it is kept
apart from STATE.md, which is replaced as the work moves.

Change it only through the spec gate, never as you go. What no longer holds is
rewritten in place, not appended to; git holds the history.

## Goal

Build `template/`: a copy-to-adopt learning-project template that works like a
local claude.ai Project, readable and writable by Claude Code, OpenCode and
DeepSeek Harness, so that switching agents by hand (e.g. when the Claude quota
runs out) loses no context. It must serve two cases: starting a new subject,
and migrating an existing claude.ai Project. Spec approved 2026-09-26,
extended the same day with migration, project instructions and Obsidian.

## Problem
Each subject needs a local space holding the material, the conversation
history and the memory. Every agent keeps its own history where the others
cannot read it, so a new agent starts with no idea where the learning stands.
The learner's existing claude.ai Projects carry long hand-written tutor
instructions that the local projects must be able to take over.

## Usage
Copy the contents of `template/` into a new folder outside this repo, put
material into `materials/sources/`, start any agent there. That is "creating
a Project". Switching projects is opening another folder.

## Structure (data contract)
```
template/
  AGENTS.md            Guard; framework (Status, start routine, Setup,
                       modes, memory rules, files, language); then
                       "Project instructions", this project's own tutor spec
  CLAUDE.md            "@AGENTS.md" only (Claude Code). OpenCode and DeepSeek
                       Harness read AGENTS.md directly.
  .vscode/settings.json  Opens blackboard.md as a rendered Markdown preview
  materials/
    sources/           The learner's originals (read-only)
    generated/         What agents produce (human-facing, edited in place)
      blackboard.md    All teaching (problem, explanation, derivation,
                       feedback), math in LaTeX; appended within a problem,
                       cleared on the next one.
                       Chat carries only short messages, no LaTeX.
      obsidian/        Obsidian-format notes; opened as a vault
  memory/
    handoff.md         Current state: where learning stands, next step,
                       current mode (+ absolute deadline date), last agent, time
    progress.md        Terse AI-facing index of what the learner knows and
                       where they struggle; points to project records if any
    decisions.md       Decisions and their reasons
    todo.md            To-dos
    sessions/          One summary per conversation:
                       YYYY-MM-DD-HHMM-<agent>.md
```

## Setup (first start, while Status says pending)
Every answer is recorded the moment it is given, so a cut-off setup resumes
without re-asking. Order: language (asked in the language of the learner's
first message), then new vs migrate.
- New: read sources; ask goal (exam / understanding / exam + understanding /
  other, with exam date), level, method, checking; draft English Project
  instructions; show a summary in the human language; write on confirmation.
- Migrate: learner supplies old instructions (paste or file) and sorts files
  themselves (originals -> sources/, earlier AI output -> generated/). Agent
  translates to English without dropping rules, rewrites claude.ai-only parts
  (knowledge search, read-only /mnt/project + present_files, "no filesystem,
  download it", other Projects, progress bookmarks), lists every adaptation
  in the human language, writes on confirmation. Current state comes from the
  learner asking the old Project "where are we, what next" and pasting the
  answer, which seeds handoff.md and progress.md.

## Precedence
Project instructions win on how to teach, including their own modes and
record systems. They never switch off the memory rules, the read-only rule for
sources/, or English for AGENTS.md and memory/, and may make "Pace and
readability" stricter but never looser.

## Pace and readability (every project, every mode)
One small piece at a time, then stop; check understanding with a short
question or small step before moving on; if lost, split smaller rather than
explain more; one question at a time; short blocks, headings, tables and
emoji signposts; the blackboard grows the same way.

## Modes (current mode stored in handoff.md)
Defaults, replaced by modes the project instructions define:
- normal: teach as the project instructions say
- sprint: e.g. "exam in 3 days"; high-yield exam content only, many exercises
- practice: nothing new; set, mark and explain exercises
Deadlines are stored as absolute dates; once passed, the agent asks whether to
return to normal.

## Update rules
| Content | How |
|---|---|
| AGENTS.md | Written by the agent during setup; afterwards only on request, except the source list when new sources appear |
| handoff.md, sessions/, progress.md, decisions.md, todo.md | Automatic, whenever state actually changes |
| "handoff" command | Optional; flushes the last stretch before a switch |
| materials/generated/ | On request, or as the project instructions direct |
| materials/sources/ | Only when the learner names a specific file |

## Language
AGENTS.md (including project instructions) and memory/: English.
Conversation and materials/generated/: the human language, asked once during
setup and recorded in Status.

## Non-goals
Quota detection, automatic switching, routing, UI, a multi-project manager,
migrating raw claude.ai conversation history, searching or indexing material,
an adopt script, sorting migrated files automatically, anything specific to
one course.

## Acceptance (each item run with the real agent; nothing counts unrun)
1. New: copy template to an empty folder, add one file to sources/, start
   Claude Code: it asks the language first, then new vs migrate, and writes
   Project instructions only after showing a summary.
2. Keep learning without saying anything about memory: handoff.md and
   sessions/ get updated.
3. Close Claude Code without a handoff, open OpenCode: it states topic, where
   learning stands, recent discussion, next step.
4. Same as 3 with DeepSeek Harness.
5. Reverse direction (OpenCode -> Claude Code) passes.
6. After a switch, the new agent does not ask for the language again; the
   current mode and deadline carry over.
7. Nothing in sources/ is modified at any point.
8. Migrate: run the learner's LeetCode / CCF CSP Project instructions through
   the migrate path. The result is English, keeps every rule, has no
   claude.ai-only mechanics left, records Traditional Chinese as the human
   language, and the agent teaches the way the original Project did.
