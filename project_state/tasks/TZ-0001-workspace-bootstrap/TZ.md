# PROF-TZ-0001 — Non-Destructive Discovery and PGSM Workspace Bootstrap

**Project:** PsychoPassport Engine (`proff`)
**Executor:** Antigravity IDE agent
**Class:** COMPLEX / Architecture + Red Team
**Status:** DRAFT FOR EXECUTION (not executed)
**Governance:** PGSM v1.0.0

## Goal

Discover and establish an isolated, minimal, auditable workspace directory hierarchy for `proff` without altering inherited settings, existing files, repositories, or personal data, and record the factual result under PGSM.

## Project Boundary

- Candidate canonical write root: `C:\Users\candy\Desktop\lil_projects\proff` (declared in `antigravity_ide_pgsm_v1_1_0.md`). Resolve its actual absolute path, existence, canonical filesystem identity, ACLs and reparse/junction/symlink status before writing.
- Permitted writes: **only** in the verified root. If root does not exist, creating precisely that final `proff` directory is permitted only when its parent already exists, is writable, and is not an unsafe link/junction; otherwise STOP with `BLOCKED_ROOT`.
- Permitted reads outside root: only IDE/OS tool versions, active/parent/global rules and Git configuration **metadata required for non-destructive discovery**. Do not copy, modify, print credentials, or read unrelated personal project content.
- All Git operations during this task are read-only (`git rev-parse`, `git status`, `git remote -v` with URLs redacted as necessary, `git config --show-origin` with secrets filtered). No init, commit, fetch, push, remote creation or credential changes.
- If the workspace is a link/junction into another directory or nested/inherited repository boundary cannot be established: STOP and report.

## Context

- The user's Grok records and screenshot describe a **knowledge-base/documentation snapshot**, not an audited local Antigravity workspace.
- `PGSM_PROJECT_STANDARD_v1.0.0.md` defines state, task, ownership and structure-version contracts.
- `00_MASTER_HANDOFF.md` proposes a generic `PROF_ROOT` hierarchy; `antigravity_ide_pgsm_v1_1_0.md` proposes a larger v1.1.0 hierarchy and a candidate Windows root. These are **design inputs, not evidence that the directories exist**.
- `CURRENT_STATE.md` from Grok (revision 3, knowledge release 1.1.0) is an imported historical artifact and must not be blindly promoted to the new workspace's live state.
- This task covers directory scaffolding and governance only, **not** scientific ingestion, Python implementation, remote GitHub, plugin cleanup, audio/video transcription, or profiling analysis.

## Assumptions

1. The Windows path above is the intended candidate; its real filesystem state remains unknown until Antigravity verifies it.
2. Knowledge-base version `1.1.0` and workspace **structure** version are independent. For a newly initialized workspace use **structure v1.0.0**. If an existing approved structure version exists, preserve it and open a separate migration decision rather than downgrade or overwrite.
3. Source files attached to the ChatGPT conversation may not exist on the Antigravity host. Absence does not authorize dummy content, reconstructed bibliography, or automatic downloads.
4. Workspace-scoped files may be created as minimal structural contracts; `.agents/` layout, active triggers, and specialized skills require later validation and will not be pre-created.
5. No real personal communications are ingested in this task.

## Scope

### Included

- Read-only discovery and inventories of workspace layout, Git isolation, applicable agent customization metadata and available project source filenames.
- Minimal PGSM bootstrap, authoritative project state, approved structure snapshot, task record and execution walkthrough.
- Minimal directories for future source/staging, specifications, pipeline modules, reports and tests as listed below (create only where indicated).
- Privacy-aware `.gitignore`, project safety `AGENTS.md`, overview `README.md`, and simple provenance/source inventory.
- Verification, hashes, no-clobber checks, explicit failure handling, and state snapshots.

### Excluded

- `pip install`, `uv sync`, Python code, ASR models, CUDA, ffmpeg downloads, automatic source download, conversion, profiling reports, science-source rewriting, new MCP/plugins/skills/rules, modifying global Antigravity configuration, Git initialization, GitHub operations, and processing live personal case data.

## Discovery Phase (must precede ALL writes)

1. Confirm `PROF_ROOT` canonical path and parent directory; classify root as `ABSENT`, `EMPTY`, or `EXISTING`.
2. Enumerate relative paths, regular files, directory links/reparse points, collisions by case, permissions, and `project_state` records if present; inventory SHA-256 of all files proposed for modification.
3. Detect ancestor/current Git root and existing remotes; do not mutate Git state. Record sanitized findings.
4. Inspect only applicable global/parent/workspace rules and installed IDE capability metadata (read-only) to determine which instructions are effective. Record `UNKNOWN` where visibility is incomplete.
5. Check whether Grok source files exist **within** verified root. Record filename, location, size and SHA-256; if absent, mark `IMPORT_PENDING` and continue the minimal scaffold. Never silently invent source contents.
6. If an existing `project_state/CURRENT_STATE.md`, task register, or structure snapshot is found, treat as existing installation: preserve all records and use next unused monotonic task ID. If a conflicting `PROF-TZ-0001` already exists, do not overwrite it; record conflict and STOP rather than reuse an ID.
7. Present any **blocking** conflict (`BLOCKED_ROOT`, `BLOCKED_GIT_BOUNDARY`, `BLOCKED_EXISTING_STATE`, `BLOCKED_PERMISSIONS`) in an evidence file and stop before mutation.

## Functional Requirements

- Current state has exactly one authoritative file: `project_state/CURRENT_STATE.md`.
- Every attempted task has a task-specific immutable `TZ.md` and a `WALKTHROUGH.md` written on completion, block, or failure when writable.
- Original source documents are never overwritten. Any future import must be byte-preserving and hash-manifested.
- Future raw case data, transcriptions, media and reports are excluded from Git by default.
- Bootstrap shall be re-entrant: rerunning checks state and does not reset records, overwrite files, or duplicate task IDs.

## Architecture / Workflow Requirements

### New-workspace physical tree, v1.0.0

```text
proff/
├── AGENTS.md
├── README.md
├── .gitignore
├── governance/
│   ├── policies/
│   │   └── privacy_boundary.md
│   └── naming.md
├── project_state/
│   ├── CURRENT_STATE.md
│   ├── ROADMAP.md
│   ├── TASK_REGISTER.md
│   ├── ISSUES.md
│   ├── DECISIONS.md
│   ├── CHANGELOG.md
│   ├── tasks/
│   │   └── TZ-0001-workspace-bootstrap/
│   │       ├── TZ.md
│   │       └── WALKTHROUGH.md
│   ├── structure/
│   │   ├── STRUCTURE.md
│   │   ├── STRUCTURE_CHANGELOG.md
│   │   └── versions/
│   │       └── v1.0.0.md
│   └── history/
│       └── state/
│           └── STATE-000001.md
├── inputs/
│   ├── source_staging/
│   │   └── .gitkeep
│   └── raw_exports/
│       └── .gitkeep
├── specifications/
│   └── knowledge_base/
│       └── README.md
├── pipeline/
│   └── README.md
├── outputs/
│   └── README.md
└── tests/
    └── README.md
```

- The above is the minimal **physical** tree for a *new* workspace. `ROADMAP.md` records future folders (`pipeline/{ingestion,conversion,transcription,analyzers,synthesis}`, `inputs/reference_library`, `specifications/schemas`, `.agents/rules`, `.agents/skills`, `.agents/agents`, `outputs/passports`, `tests/unit`) without creating empty placeholders in this task.
- Where the approved roadmap and this tree differ, this tree defines only the phase-1 physical state, not the final planned product structure.
- `specifications/knowledge_base/README.md` states `IMPORT_PENDING` and references the actual source-inventory location, without any invented Grok content.
- `project_state/ROADMAP.md` captures the phase plan provided with this task, adapted to *verified* local facts only.
- `AGENTS.md` contains brief invariant and startup order: read privacy boundary, current state, roadmap/task register, active TZ, current structure. Do not claim `.agents` discovery conventions without testing.
- `project_state/CURRENT_STATE.md` has factual values for structure version, state revision, active task, status, blocking issues, last completed task, next action, timestamps with offset; status changes only after corresponding validation.
- `project_state/structure/STRUCTURE.md` lists the real physical directories. Initial snapshot v1.0.0 is immutable; structure changelog records initialization.
- `project_state/TASK_REGISTER.md` is an index; task instructions reside solely in task-specific `TZ.md`. If this TZ was provided as a file inside the workspace, preserve the exact text; otherwise record source and copy the approved content with hash, no paraphrase.
- `project_state/ISSUES.md` and `DECISIONS.md` are indexes; do not create fictitious issues or ADRs. Optional `LESSONS.md`, `archive`, `.agents`, other scopes are deferred.
- Source inventory is in the task `WALKTHROUGH.md` or `EVIDENCE.md` if necessary; it records only observed paths and hashes. No sensitive full-text copying into reports.

### Ownership / state

- `governance`: project safety/naming rules.
- `project_state`: canonical live state, immutable history, tasks and versioned structure.
- `inputs`: authorized original or future staged material; raw cases never Git-tracked.
- `specifications`: future schemas and authoritative KB imports, not a parallel live state.
- `pipeline`: future executable code, currently explanatory README only.
- `outputs`: future derived artifacts, by default untracked.
- `tests`: future reproducible tests, currently explanatory README only.
- Single writer for `CURRENT_STATE.md`; write to a temp file within root and replace atomically where supported.
- For any failure before the final state update, preserve evidence, mark `BLOCKED` or `FAILED` without inventing validation success, and do not auto-delete existing files.

## Invariants

1. `PROF_ROOT` is the only write boundary; no link/junction escape.
2. No existing file is silently overwritten; no previous PGSM history is discarded.
3. `CURRENT_STATE.md` is the only live status SSOT; old Grok `CURRENT_STATE.md` is reference material only.
4. Original evidence is immutable; its byte hash is the primary identity.
5. No secrets, raw chat exports, audio, video, case reports, transcriptions, personal data, downloaded full-text PDFs, or caches are staged for Git.
6. Stage completion is an evidence-backed fact, never assumed from file presence alone.
7. No public network calls or config mutations outside approved root.

## Implementation Steps

1. Complete read-only Discovery Phase and save a sanitized preflight inventory after the root boundary is validated.
2. If root is absent and parent validation passes, create only the final approved `proff` directory. If root exists, preserve all content.
3. Determine bootstrap branch `NEW` vs `EXISTING`; for existing PGSM perform compatibility assessment and stop at any conflicting canonical ownership/version without migrating.
4. Create the required minimal directories with collision/no-clobber checks. Create `.gitkeep` only in allowed ignored input directories.
5. Write `.gitignore` **before any future Git action**: exclude `.env`, `.env.*` (allow `.env.example` only when no secrets), credentials, secrets, `.venv/`, `__pycache__/`, `.pytest_cache/`, `.cache/`, `.tmp/`, `inputs/raw_exports/**` (with exception for `.gitkeep`), `inputs/source_staging/**` (with `.gitkeep` exception), `inputs/reference_library/pdf/**`, `inputs/reference_library/extracted_text/**`, `outputs/**` (exception for `outputs/README.md`), other case transcripts and local case payload folders. Do not use blanket ignores that hide governance files.
6. Write concise `README.md`, `AGENTS.md`, `governance/policies/privacy_boundary.md`, `governance/naming.md`; no clinical methods, inferred psychometric formulas or new role agents.
7. Copy the approved roadmap into `project_state/ROADMAP.md`; list first and future phases as `NOT_STARTED` unless verified otherwise.
8. Create PGSM indexes and actual current structure version file/snapshot/changelog; never declare unused future dirs physically present.
9. Create `TZ.md` at `project_state/tasks/TZ-0001-workspace-bootstrap/` (or previously determined next unique ID for existing state); register exactly once. Preserve task source text and hash.
10. Create factual initial state and immutable `STATE-000001.md` snapshot for newly initialized workspace. Use actual offset-aware timestamp; ensure revision increments correctly with task transition and completion.
11. Run structural, privacy, boundary, and idempotency validations. Record checks with PASS/FAIL/NOT_RUN, exact command/test evidence and no sensitive text.
12. Create per-task `WALKTHROUGH.md`; on successful checks mark task `COMPLETED`, update register and live current state, append final immutable state snapshot with the next unused `STATE-XXXXXX` number. On failure preserve partial outcomes and record `BLOCKED`/`FAILED` instead.
13. Report the exact paths created/changed, current state revision and structure version, discovered Git boundary, source-import status, open issues and the next task. Do not claim GitHub/AI/library integration succeeded.

## Allowed Changes

- Create/modify only newly initialized *local* PGSM and minimal tree files listed above, or append/patch verified existing nonconflicting PGSM records after a no-clobber check.
- Record redacted inventory and local SHA-256 hashes in task evidence files.

## Forbidden Changes

- Modifying any other workspace, ancestor directory content (except creating the precise absent `proff` directory), global IDE settings, existing Git histories, upstream remotes, credentials, plugins, installed skills, and MCP servers.
- Deleting, moving, normalizing, rewriting or auto-downloading Grok files, bibliography, case records, media or unrelated files.
- Installing dependencies, generating Pydantic models, claiming scientific-source verification, or recording test passes without tests.
- Writing a second canonical current state or overwriting old tasks/walkthroughs.

## Edge Cases and Failure Handling

- Missing parent directory, lack of permissions, reparse-point escape: `BLOCKED_ROOT`, no writes.
- Existing unrelated files or PGSM with incompatible rules: inventory them; no forced migration; `BLOCKED_EXISTING_STATE`.
- Existing task ID conflict: refuse ID reuse; preserve originals and request owner decision if identity or scope cannot be established.
- Inherited/ancestor Git: read-only discovery; record containment; never `git init`.
- Disk full, interrupted writes: use atomic temp-then-replace for canonical state; retain checkpoint/evidence and resume without rewriting immutable snapshots.
- Source files not present: `IMPORT_PENDING`; bootstrap may complete without them.
- Privacy control unknown: no sensitive imports, no cloud operations.

## Security Requirements

- Strict path canonicalization, reparse-point detection, no cross-boundary write.
- Principle of least privilege; no automatic external network connections.
- Ignore local case data, media and secrets; test that a synthetic probe path under ignored directories is not eligible for tracking (read-only `git check-ignore` if Git already exists, otherwise validate with local pattern evaluation and mark Git-specific test `NOT_RUN`).
- No source content or credentials in status/evidence logs; only hashes and redacted paths where necessary.

## Definition of Done — binary acceptance

1. Exact resolved root path is recorded with `ROOT_BOUNDARY=PASS`, or the task is explicitly `BLOCKED_ROOT` and not `COMPLETED`.
2. Every directory and file in the phase-1 physical tree exists as listed; the actual structure tree and structure snapshot agree (filesystem enumeration + diff = no undocumented tracked dirs).
3. `CURRENT_STATE.md` is the single authoritative live state; no newly created parallel `STATUS.md`/`HANDOFF_SNAPSHOT.md` files.
4. One unique registered task record exists with its exact `TZ.md`, and its `WALKTHROUGH.md` lists observed changes and actual test outcomes.
5. For the new workspace: `STRUCTURE.md`, immutable `versions/v1.0.0.md`, `STRUCTURE_CHANGELOG.md`, initial/final immutable state snapshots exist with unique identifiers; structure version is `1.0.0`.
6. `.gitignore` has no sensitive-data false negative in all defined synthetic path tests; protected index files remain eligible for version control.
7. Pre/post inventory reports show no modification to pre-existing source files, parent/Git metadata or inherited configuration; any unreadable external condition marked `UNKNOWN`, not `PASS`.
8. No dependencies installed, no network activity initiated, no Git mutation performed by this task.
9. Re-run preflight confirms no task ID reused and no overwrites; if run against an already completed bootstrap, return `ALREADY_BOOTSTRAPPED` rather than reconstructing state.
10. Task `COMPLETED` only if checks 1–9 pass; otherwise `BLOCKED` or `FAILED` with exact unresolved condition.

## Self Validation

- Run PowerShell read-only inventory (e.g. `Get-ChildItem -Force -Recurse`, excluding dangerous link traversal); compare actual paths against phase-1 tree.
- Use `Get-FileHash -Algorithm SHA256` on any preserved pre-existing source and candidate for modification; compare hashes before and after.
- Verify `git rev-parse --show-toplevel` is read-only and any inherited Git metadata unchanged; `git status --porcelain` may be used if repository exists.
- Confirm state revision progression and snapshot immutability; verify every filename reference resolves locally or is explicitly labelled `PLANNED` / `IMPORT_PENDING`.
- Execute deterministic synthetic ignore-pattern tests without creating sensitive real data.
- Record PASS, FAIL, or NOT_RUN separately; never infer successful testing from expected behavior.
- If any instruction is ambiguous or conflicts with an invariant, STOP and request a decision instead of guessing.

## Required final handoff from Antigravity

Return `ROOT`, `TASK_ID`, `OUTCOME`, `STRUCTURE_VERSION`, `STATE_REVISION`, `GIT_BOUNDARY`, `KB_IMPORT_STATUS`, `CREATED_PATHS`, `MODIFIED_PATHS`, `TEST_RESULTS`, `BLOCKING_ISSUES`, `NEXT_TASK`; every claimed completion must link to actual workspace-local evidence.
