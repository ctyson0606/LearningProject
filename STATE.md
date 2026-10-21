# STATE

> Last updated: 2026-10-21

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
   check the pickup (acceptance 3 with the same agent; later sessions there
   did pick up from handoff.md). Also confirm the UK date rule (2026-10-02)
   on the Mac: its first session there must name its file
   YYYY-MM-DD-NN-<agent>.md with the UK date and write no clock times; the
   TZ command has only been run on Windows.
2. Acceptance 8, audited 2026-10-04 (Sonnet subagent read the original
   instructions and the migrated Project instructions in LeetCode-CCFCSP;
   10 random original rules spot-checked by hand, all present): about 150
   rules checked, none missing, weakened or changed; English throughout;
   Status records Traditional Chinese; no claude.ai mechanics left; original
   sections 1-11 kept in order. Still open: "teaches the way the original did"
   cannot be judged, because no problem has been taught there yet. Seven
   claude.ai adaptations were correct but recorded nowhere; on 2026-10-04 they
   were added to LeetCode-CCFCSP memory/decisions.md, and the template's
   migrate path now has the agent record the list in decisions.md.
3. Acceptance 3 and 4 were run on 2026-10-21 (see Recent Decisions) on a
   scratchpad clone of MATH2121, one-shot runs (`opencode run`, `dsh
   --profile headless`), not the interactive UIs. Still open: acceptance 5
   (OpenCode or Harness -> Claude Code) and a run in the interactive UIs
   (OpenCode TUI, Harness web at `npx @deepseek-ai/dsh web`, port 3080).
   The Harness headless profile does not see a key saved on the web Models
   page; it needs DEEPSEEK_API_KEY in the environment.
4. Confirm the template guard for DeepSeek Harness inside this repo; Claude
   Code and OpenCode (2026-10-21, nemotron) have been probed and hold.

## Open Questions
- The 30-minute open-session check gives false positives: at 15:13 BST on
  2026-10-21 something (probably the share sync or a git operation) touched
  the mtime of almost every file in COMP2012H, ECON1221, MATH2121 and
  PHYS1002 with git status clean, so `find memory/sessions -mmin -30` listed
  old session files. The learner chose to leave it as is for now
  (2026-10-21); possible fix: check only the newest session file, or also
  require uncommitted changes.
- Can OpenCode and DeepSeek Harness read PDFs in materials/sources/? Claude
  Code can (20 pages per read), and in MATH2121 it extracted text with pypdf
  instead. If the others cannot, sources may need converting to text on
  adoption.

## Known Annoyances

## Recent Decisions
- 2026-10-21 agent test, learner approved the two template changes it led
  to. Each run started on a clean clone of MATH2121 with "我回來了", then
  "the det swap sign slipped; back to normal mode"; every claimed edit was
  checked against git. OpenCode + nemotron-3-ultra-free (free; 4 of 5 free
  models were rate-limited) and OpenCode + local qwen3.6:27b read memory and
  asked the right question, but skipped the session file, the full start
  report and the size check, and nemotron claimed an edit it never made.
  OpenCode + DeepSeek V4.1 Flash 1017 (`deepseek/deepseek-flash`) did
  nearly everything and committed on its own, but wrote a clock time,
  edited AGENTS.md without asking and skipped the size check. DeepSeek
  Harness + the same model was the most compliant (the only one to run the
  size check; no clock time; AGENTS.md untouched; own commit under UK TZ;
  reused mistake 71 instead of a new number) but created its session file
  only in the second turn. So compliance depends mainly on the model, and
  DeepSeek V4.1 Flash is a usable fallback when the Claude quota runs out.
  Two faults every agent showed became template changes, synced into all
  six projects: the session file is now created at start step 4, before the
  first reply, so a session cut off after one reply leaves a trace; and the
  progress.md note rule now carries a right and a wrong example, because
  every model added a dated "recurred in the midterm" phrase to the note.
  Retest the same day on the synced framework, DeepSeek V4.1 Flash in both
  agents: both created the session file before the first reply, ran the
  size check, wrote no clock times and asked before retiring midterm-only
  material. The note fix worked in OpenCode ("cost marks in the midterm",
  no date) but not in Harness ("recurred in the 2026-10-21 midterm").
  Harness committed after each turn; OpenCode did not commit at all.
  Learner approved two more template changes, synced into all six
  projects (not yet retested): the agent checks the Note for a YYYY-MM-DD
  date before saving and takes it out; and it commits right after every
  write to memory/, instead of when a piece of work "is finished", which
  left the decision to the model.
- 2026-10-21, learner approved after a post-midterm review of all six
  projects (all following the rules: UK dates, session names, sources
  untouched, no cross-project edits, handoff.md within 40 lines). Template
  changes, synced into all six AGENTS.md files: start reads only the last 40
  lines of the newest session file (they had grown to 20-27 KB); start checks
  AGENTS.md size and proposes moving a task-specific section to memory/
  above 60,000 bytes; a passed deadline also prompts removing deadline-only
  Project instructions; progress.md notes about 30 words, rewritten; revealed
  agent-only files are deleted; a Git section (the agent commits on its own
  after each finished piece, never pushes, never records commits in memory;
  the learner chose own commits for every project, COMP2012H included,
  replacing its 2026-10-09 "only when asked" rule). Reasons: COMP2012H AGENTS.md was 66,783 bytes
  on disk, over DeepSeek Harness's cap; MATH2121 and COMP2012H kept midterm
  dates and sprint rules after the exams; their progress.md notes had become
  logs (12 KB each); COMP2012H had 25 agent-only key files; MATH2121 and
  COMP2012H each invented a git rule after commit-logging churn. Per
  project: COMP2012H §8 and §11 moved verbatim to memory/exam-prep-mode.md and
  memory/knowledge-links.md (now about 56 KB), stale §1 rows removed and
  §18 Git removed; MATH2121 midterm line and sprint exception and its Git section
  removed; both progress.md files rewritten; both decisions.md record it.
  The 22 revealed COMP2012H answer-key files were deleted (learner approved);
  adt-drill-key (unrevealed errata), u3-array-drill-key and u7-drill-key kept.
  Committed in all six D:\Learning projects on 2026-10-21, not pushed
  (learner's instruction).
- One project, one session (2026-10-04, learner approved): an agent edits
  only its own project, and at start asks the learner if a session file
  changed in the last 30 minutes (another session may be open). Reason: on
  2026-10-01 a session opened in LeetCode-CCFCSP edited MATH2121 while
  MATH2121's own session was running; a rule was added, removed and replaced,
  and both logs ended up in one session file. The 30-minute window, rather
  than "any session today", avoids asking on every quota-driven agent switch.
- Agent-only content (answer keys, sealed specs) lives in memory/, in
  English, never in materials/generated/, which the learner browses; it is
  revealed on the blackboard (2026-10-02, learner approved). PHYS1002 already
  kept its mock-test key in memory/; LeetCode's Track C sealed spec moved from
  materials/generated/TrackC-封存規格.md to memory/trackc-sealed-spec.md
  (no round had been run, so no file existed).
- 2026-10-04, learner approved: COMP2012H's AGENTS.md had reached 64,908
  bytes, about 600 under DeepSeek Harness's 64 KiB cap, so its "Past papers
  and question bank" section (6,308 bytes, reference used only when choosing
  originals or preparing exams) moved verbatim to memory/past-papers.md,
  leaving a pointer; AGENTS.md is now 58,945 bytes. The template gained a
  .gitignore for OS metadata; all six projects got it, the ._*, .DS_Store
  and .smbdelete* files (MATH2121 59, Robomaster 2) were deleted, and the
  desktop.ini files in COMP2012H (21) and PHYS1002 (69) sources were untracked
  but kept on disk. The Mac keeps writing ._* files over the share; git now
  ignores them and Obsidian hides dotfiles. Executed by a Sonnet subagent,
  checked independently afterwards.
- handoff.md has a fixed shape (Now, Next step, Paused; at most 40 lines) and
  is rewritten whole; progress.md is one row per topic plus recurring
  patterns; Project instructions hold only what stays true, and a replaced
  rule is rewritten in place (2026-10-02, learner approved). Reason: in
  D:\Learning agents patched handoff.md instead of overwriting it (MATH2121
  contradicted itself, Robomaster had two sections fused), logged every
  answer in progress.md (Robomaster 20 KB), and left plans and superseded
  rules in Project instructions (MATH2121 kept both "LaTeX in conversation"
  and "no LaTeX in chat"). Rolled out the same day: framework synced, all
  twelve files rewritten to the new shapes. Project instructions cleaned in
  MATH2121 (LaTeX contradiction, learner-level snapshot, current plan, deleted
  sources, PDF reading), Robomaster (learner level, code-project facts moved
  out of handoff.md) and PHYS1002 (cheat-sheet regeneration moved out of
  handoff.md, the duplicate no-clock-times rule dropped), learner approved.
- Pace and readability is a framework rule that project instructions can
  tighten but not loosen: the learner asked (2026-09-27) for less taught at
  once, more emoji, readability, and a confirmed understanding before each
  next step, as a baseline across projects rather than a per-project choice.
- Dates only, no clock times, and every date is the UK date read with
  `TZ='GMT0BST,M3.5.0/1,M10.5.0' date` (PowerShell: ConvertTimeBySystemTimeZoneId
  'GMT Standard Time'), never the system clock (learner, 2026-10-02). The
  learner's Windows runs in UK time and their Mac in Hong Kong time, so
  Robomaster, MATH2121 and LeetCode mixed both in one file, and PHYS1002 had
  already banned clock times. Session files became YYYY-MM-DD-NN-<agent>.md,
  and decisions.md went oldest first, because agents appended at the bottom
  in three of six projects although it said newest first.
- 2026-10-02 rollout to all six projects in D:\Learning, committed there (no push):
  framework part of AGENTS.md synced; every clock time removed from memory/
  and Project instructions; session files renamed; decisions.md reordered
  oldest first. Dates were checked against git commit times (absolute even
  when the zone label was wrong) and none crossed midnight in UK time.
  Three sessions whose zone could not be settled (PHYS1002 2026-09-29-01,
  MATH2121 2026-09-27-02, LeetCode 2026-09-27-01) keep their dates as
  written: the learner said order is what matters, not the exact day.
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
