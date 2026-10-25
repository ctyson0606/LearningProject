# SPEC

The contract this project is built against: what the spec gate produced and a
person approved. It stays true for as long as the code does, so it is kept
apart from STATE.md, which is replaced as the work moves.

Change it only through the spec gate, never as you go, except a goal's How and
Parts lines, written once its criteria all have evidence. What no longer holds
is rewritten in place, not appended to; git holds the history.

## Goals

Build `template/`: a copy-to-adopt learning-project template that works like a
local claude.ai Project, readable and writable by Claude Code, OpenCode and
DeepSeek Harness, so that switching agents by hand (e.g. when the Claude quota
runs out) loses no context. It must serve two cases: starting a new subject,
and migrating an existing claude.ai Project. Spec approved 2026-09-26,
extended the same day with migration, project instructions and Obsidian.

- G1 (M1): Start a new subject: copy the template into a folder, add the
  material, and the agent sets the project up by asking the language, the
  goal and how the learner likes to learn, showing a summary to approve.
  - How: The template's AGENTS.md carries a start routine and a setup that
    asks the language first, then new or migrate, and writes the project's
    instructions only after the learner approves a summary of them.
  - Parts: C1, C2
- G2 (M1): The agent keeps the memory as it teaches, without being asked, so
  where the learning stands is always on disk.
  - How: The memory rules in AGENTS.md tell the agent to rewrite handoff.md
    and add to the session file the moment something changes, and to commit
    after every memory write.
  - Parts: C1, C3
- G3 (M1): Switch agents at any time — Claude Code, OpenCode, DeepSeek
  Harness — and the new one picks up where the last one stopped.
  - How: Every agent reads the same plain files: the start routine reads
    handoff.md, progress.md, the to-do list and the end of the last session
    file, then states where the learning stands. The rules live in AGENTS.md,
    which all three agents load by themselves.
  - Parts: C1, C2, C3
- G4 (M1): Move an existing claude.ai Project in: its instructions, its
  material and where the learning stood.
- G5 (M1): The learner's own material is never changed.

## Problem
Each subject needs a local space holding the material, the conversation
history and the memory. Every agent keeps its own history where the others
cannot read it, so a new agent starts with no idea where the learning stands.
The learner's existing claude.ai Projects carry long hand-written tutor
instructions that the local projects must be able to take over.

## Milestones

- M1: v1 — the learning-project template

## Usage
Copy the contents of `template/` into a new folder outside this repo, put
material into `materials/sources/`, start any agent there. That is "creating
a Project". Switching projects is opening another folder.

## Components

- C1: Template rules (`template/AGENTS.md`) — the start routine, setup, modes and memory rules every agent follows
- C2: Claude Code pointer (`template/CLAUDE.md`) — sends Claude Code to the template's AGENTS.md; uses C1
- C3: Memory (`template/memory/`) — handoff, progress, decisions, to-dos and session files that every agent reads and writes
- C4: Materials (`template/materials/`) — the learner's sources, never modified, and what the agent makes, the blackboard included
- C5: Blackboard view (`template/.vscode/settings.json`) — opens the blackboard as a rendered preview with math on

## Structure (data contract)
```
template/
  AGENTS.md            Guard; framework (Status, start routine, Setup,
                       modes, memory rules, files, language); then
                       "Project instructions", this project's own tutor spec
  CLAUDE.md            "@AGENTS.md" only (Claude Code). OpenCode and DeepSeek
                       Harness read AGENTS.md directly.
  .vscode/settings.json  Opens blackboard.md as a rendered Markdown preview
  .gitignore           OS metadata (._*, .DS_Store, .smbdelete*, desktop.ini,
                       Thumbs.db) never enters git
  materials/
    sources/           The learner's originals (read-only)
    generated/         What agents produce (human-facing, edited in place)
      blackboard.md    All teaching (problem, explanation, derivation,
                       feedback), math in LaTeX; appended within a problem,
                       cleared on the next one.
                       Chat carries only short messages, no LaTeX.
      obsidian/        Obsidian-format notes; opened as a vault
  memory/
    handoff.md         Current state only, rewritten whole, at most 40
                       lines: Updated, Agent, Mode, Deadline; Now, Next
                       step, Paused
    progress.md        AI-facing index: one row per topic (✅/🟡/❌; a note
                       of about 30 words, rewritten, never appended to)
                       plus recurring patterns; points to project records
                       if any
    decisions.md       Decisions and their reasons, oldest first
    todo.md            To-dos
    <agent-only>.md    Anything the learner must not see yet (answer keys,
                       sealed specs); first line says agent-only, named in
                       handoff.md while in use, revealed on the blackboard,
                       deleted once fully revealed
    sessions/          One summary per conversation:
                       YYYY-MM-DD-NN-<agent>.md (NN = order within the day)
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
  download it", other Projects, progress bookmarks), lists every adaptation in
  the human language, writes on confirmation and records the list in
  decisions.md. Current state comes from the learner asking the old Project
  "where are we, what next" and pasting the answer, which seeds handoff.md and
  progress.md.

## Precedence
Project instructions win on how to teach, including their own modes and
record systems. They never switch off the memory rules, the UK date rule,
the one-project-one-session rule, the read-only rule for sources/, or English
for AGENTS.md and memory/, and may make "Pace and readability" stricter but
never looser. They hold only what stays true for the whole course; plans and
progress live in memory/, and a rule that replaces another is rewritten in
place.

## One project, one session
An agent edits only the project it runs in; work for another project is done
by a session opened there. At start it checks for another open session (a
session file changed in the last 30 minutes) and asks the learner before
changing anything. Learner's request, 2026-10-04, after two sessions edited
MATH2121 at once on 2026-10-01.

## Time (every project, no exceptions)
Dates only, never clock times, in files, file names, deadlines and messages.
Every date is the UK date (Europe/London), read fresh from a command that
forces that zone, whatever the computer is set to; git commits run under the
same zone. Order replaces the clock: session files are numbered within the
day, and entries inside a file go oldest first. Dates given in another zone
are converted to the UK date. Learner's request, 2026-10-02: their computers
run in different zones (Windows UK, Mac Hong Kong).

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
Deadlines are stored as absolute UK dates; once passed, the agent asks whether
to return to normal and names the parts of Project instructions that served
only that deadline (date, logistics, sprint rules, schedules), removing them on
agreement.

## Size limit
At every start the agent checks AGENTS.md; above 60,000 bytes it tells the
learner and proposes moving a section needed only for one kind of task
verbatim into memory/, leaving a pointer that says when to read it. DeepSeek
Harness reads at most 65,536 bytes of instruction files and drops the rest.
Learner's review, 2026-10-21: COMP2012H had reached 66,783 bytes.

## Git
The agent commits on its own right after every write to memory/, only this
project's files, never pushing, unless Project instructions say otherwise.
Commits are never recorded in memory files.
Learner's review, 2026-10-21: MATH2121 and COMP2012H each invented the
no-logging rule after commit-logging churn; the learner chose own commits as
the default.

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

## Acceptance criteria

Each item is run with the real agent; nothing counts unrun.

1. AC1 (G1) New: copy template to an empty folder, add one file to sources/, start
   Claude Code: it asks the language first, then new vs migrate, and writes
   Project instructions only after showing a summary.
2. AC2 (G2) Keep learning without saying anything about memory: handoff.md and
   sessions/ get updated.
3. AC3 (G3) Close Claude Code without a handoff, open OpenCode: it states topic, where
   learning stands, recent discussion, next step.
4. AC4 (G3) Same as 3 with DeepSeek Harness.
5. AC5 (G3) Reverse direction (OpenCode -> Claude Code) passes.
6. AC6 (G3) After a switch, the new agent does not ask for the language again; the
   current mode and deadline carry over.
7. AC7 (G5) Nothing in sources/ is modified at any point.
8. AC8 (G4) Migrate: run the learner's LeetCode / CCF CSP Project instructions through
   the migrate path. The result is English, keeps every rule, has no
   claude.ai-only mechanics left, records Traditional Chinese as the human
   language, and the agent teaches the way the original Project did.
