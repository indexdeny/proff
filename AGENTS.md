# AGENTS.md — Agent Operating Instructions & Invariants

**Project:** PsychoPassport Engine (`proff`)  
**Governance:** PGSM v1.0.0  
**Structure Version:** v1.0.0  
**Canonical Write Boundary:** `C:\Users\candy\Desktop\lil_projects\proff`

---

## 1. Startup Order

Any agent operating in this workspace MUST follow this deterministic startup sequence before proposing or executing changes:

1. **Privacy Boundary**: Read and enforce [`governance/policies/privacy_boundary.md`](governance/policies/privacy_boundary.md). Confirm that all raw data and private communication cases remain isolated.
2. **Current State (SSOT)**: Read [`project_state/CURRENT_STATE.md`](project_state/CURRENT_STATE.md). Verify current state revision, active task, and blocking issues.
3. **Roadmap & Tasks**: Review [`project_state/ROADMAP.md`](project_state/ROADMAP.md) and [`project_state/TASK_REGISTER.md`](project_state/TASK_REGISTER.md) to understand overall milestones and task progression.
4. **Active Task Specification**: Read the designated task specification at `project_state/tasks/<active-task-id>/TZ.md`. Never execute actions outside an approved TZ.
5. **Structure Baseline**: Inspect [`project_state/structure/STRUCTURE.md`](project_state/structure/STRUCTURE.md) and [`project_state/structure/versions/v1.1.0.md`](project_state/structure/versions/v1.1.0.md) to ensure physical directory invariants are maintained.
6. **Git Policy & Versioning**: Read and enforce [`governance/git_policy.md`](governance/git_policy.md) and [`.agents/rules/03-git-checkpoints.md`](.agents/rules/03-git-checkpoints.md) before executing version control operations.

---

## 2. Workspace Invariants

1. **Boundary Lockdown**: The only authorized write root is `C:\Users\candy\Desktop\lil_projects\proff`. Traversal across symlinks, reparse points, or junctions outside this root is strictly forbidden.
2. **Single Source of Truth**: `project_state/CURRENT_STATE.md` is the only live status authority. No parallel status files (`STATUS.md`, `HANDOFF_SNAPSHOT.md`) may be created.
3. **Non-Destructive Operations**: Pre-existing files and original evidence are immutable. Never delete, overwrite, or clobber existing source files or prior PGSM history snapshots.
4. **Strict Privacy & Data Containment**: Raw case exports (`tg_save/`, `inputs/raw_exports/`), audio/video files, personal communications, and credentials are never tracked in Git and never sent over public networks.
5. **No Medical / Diagnostic Claims**: The engine is an observational communication pattern analysis tool. Agents must never generate clinical psychiatric diagnoses or unverified psychometric claims.
6. **Verifiable Evidence Gate**: Task completion is an evidence-backed fact established by automated validation checks, never assumed from file presence alone.
7. **Git Checkpoint Control**: Staging must be selective and task-scoped. Destructive Git operations (`reset --hard`, `push --force`) are prohibited. Remote operations require explicit human authorization.

