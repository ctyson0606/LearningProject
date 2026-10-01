# STATE

> Last updated: 2026-10-01

Current working state. Superseded content is deleted, not archived.
For durable rules see METHOD.md.

## Current Focus

Building `template/` to the spec in SPEC.md, approved 2026-09-26 and
extended the same day with migration, project instructions and Obsidian.
The spec moved there from this file on 2026-10-01, when the framework gave
it a file of its own.

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
- Pace and readability is a framework rule that project instructions can
  tighten but not loosen: the learner asked (2026-09-27) for less taught at
  once, more emoji, readability, and a confirmed understanding before each
  next step, as a baseline across projects rather than a per-project choice.
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

## Upstream
