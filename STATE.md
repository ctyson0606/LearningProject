# STATE

> Last updated: 2026-09-26

Current working state. Superseded content is deleted, not archived.
For durable rules see METHOD.md.

## Current Focus

Build `template/`: a copy-to-adopt learning-project template that works like a
local claude.ai Project, readable and writable by Claude Code, OpenCode and
DeepSeek Harness, so that switching agents by hand (e.g. when the Claude quota
runs out) loses no context. It must serve two cases: starting a new subject,
and migrating an existing claude.ai Project. Spec approved 2026-09-26,
extended the same day with migration, project instructions and Obsidian.

### Problem
Each subject needs a local space holding the material, the conversation
history and the memory. Every agent keeps its own history where the others
cannot read it, so a new agent starts with no idea where the learning stands.
The learner's existing claude.ai Projects carry long hand-written tutor
instructions that the local projects must be able to take over.

### Usage
Copy the contents of `template/` into a new folder outside this repo, put
material into `materials/sources/`, start any agent there. That is "creating
a Project". Switching projects is opening another folder.

### Structure (data contract)
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
                       feedback), math in LaTeX; overwritten per problem.
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

### Setup (first start, while Status says pending)
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

### Precedence
Project instructions win on how to teach, including their own modes and
record systems. They never switch off the memory rules, the read-only rule for
sources/, or English for AGENTS.md and memory/.

### Modes (current mode stored in handoff.md)
Defaults, replaced by modes the project instructions define:
- normal: teach as the project instructions say
- sprint: e.g. "exam in 3 days"; high-yield exam content only, many exercises
- practice: nothing new; set, mark and explain exercises
Deadlines are stored as absolute dates; once passed, the agent asks whether to
return to normal.

### Update rules
| Content | How |
|---|---|
| AGENTS.md | Written by the agent during setup; afterwards only on request, except the source list when new sources appear |
| handoff.md, sessions/, progress.md, decisions.md, todo.md | Automatic, whenever state actually changes |
| "handoff" command | Optional; flushes the last stretch before a switch |
| materials/generated/ | On request, or as the project instructions direct |
| materials/sources/ | Only when the learner names a specific file |

### Language
AGENTS.md (including project instructions) and memory/: English.
Conversation and materials/generated/: the human language, asked once during
setup and recorded in Status.

### Non-goals
Quota detection, automatic switching, routing, UI, a multi-project manager,
migrating raw claude.ai conversation history, searching or indexing material,
an adopt script, sorting migrated files automatically, anything specific to
one course.

### Acceptance (each item run with the real agent; nothing counts unrun)
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

## Next Steps
1. Learner's first real project, D:\Learning\MATH2121 (Claude Code, new path,
   2026-09-26), showed acceptance 1 and 2 in its files: language asked first,
   draft confirmed before writing, exam date stored absolute, all memory
   files updated unprompted, the blackboard convention written into Project
   instructions. Still open there: close Claude Code and start a fresh one to
   check the pickup (acceptance 3 with the same agent), and confirm the
   timestamp fix on a project adopted after this change.
2. Install OpenCode and DeepSeek Harness (neither is installed on this machine
   as of 2026-09-26).
3. Run the remaining acceptance items with the real agents. Also confirm the
   template guard holds for OpenCode and DeepSeek Harness inside this repo;
   only Claude Code has been probed.

## Open Questions
- Can OpenCode and DeepSeek Harness read PDFs in materials/sources/? Claude
  Code can (20 pages per read), and in MATH2121 it extracted text with pypdf
  instead. If the others cannot, sources may need converting to text on
  adoption.

## Known Annoyances

## Recent Decisions
- Every timestamp is read from the system clock at the moment it is written,
  not only at session start: in MATH2121 handoff.md said "Updated: 23:40"
  while the file was written at 23:05 and the clock read 23:08.
- All teaching goes on materials/generated/blackboard.md, in every subject,
  with .vscode/settings.json opening it as a rendered preview; chat keeps only
  short messages. The Claude Code chat panel in VS Code and terminal agents
  do not render LaTeX, and the learner asked for all generated teaching on
  the board, not only math. Taken from the working setup the agent
  built in MATH2121 (which used 黑板.md); the template name is English
  because the template serves every language.
- A lasting change the learner agrees to (how to teach or present) goes into
  Project instructions at once, since the next agent always loads that
  section but reads decisions.md only when an earlier choice matters. The
  MATH2121 agent already did this unprompted; the rule makes it explicit.
- Project instructions live in a section of AGENTS.md, not a separate file:
  OpenCode and DeepSeek Harness do not resolve imports, so a separate file
  would load only if the agent remembered to read it. DeepSeek Harness caps
  auto-loaded instructions at 64 KiB in total and truncates beyond that
  (packages/bundle/base/cordis.patch.yml:291, commit 477b4f4); the learner's
  longest existing instructions are an estimated 30-35 KiB in Chinese, less
  once translated.
- Migration carries instructions, files and a pasted state summary, not raw
  conversation history: the claude.ai export is one large JSON for the whole
  account, and a "where are we, what next" answer seeds handoff.md directly.
- template/AGENTS.md opens with a guard instead of storing the entry files
  under other names: both Claude Code (probed) and DeepSeek Harness (source)
  load nested instruction files while this repo edits template/, and renaming
  would break "adopt = copy". Two fresh Claude Code runs in this repo loaded
  the template files and did not act on them.
- Entry files are AGENTS.md plus a CLAUDE.md stub, no DeepSeek-specific file:
  DeepSeek Harness loads every existing AGENTS.md and CLAUDE.md by default and
  does not resolve "@file" imports (packages/context/agent-instructions/src/
  config.ts, commit 477b4f4).
- Memory files update automatically rather than only on "handoff": the Claude
  quota can run out mid-conversation, after which the agent cannot be asked
  to hand off.
- materials/ is split into sources/ and generated/: a copied template may have
  no git, so an overwritten original could not be recovered.
- Environment facts set to "none": the deliverable is Markdown only, with no
  code to install, build, lint or test; acceptance is manual runs with the
  real agents.
