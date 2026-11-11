# File Classification Manifest for Git Tracking

**Task ID:** `TZ-0003-isolated-git-checkpoints`  
**Phase:** PH-03  
**Date:** 2026-11-12T00:56:30+02:00  
**Project:** PsychoPassport Engine (`proff`)  
**Standard:** PGSM v1.0.0 / `governance/policies/privacy_boundary.md`  

---

## 1. Classification Categories

- **`GIT_REQUIRED`**: Core governance, specifications, task records, PGSM state, structure contracts, source specifications, rules, keep-files, and documentation.
- **`GIT_EXCLUDED`**: Sensitive personal communication archives, media recordings, backup zip archives, temporary test files, caches, secrets.
- **`REVIEW_REQUIRED`**: Files of uncertain origin or sensitivity; requires explicit audit before staging.

---

## 2. Classification Inventory

| Relative Path / Pattern | Category | Rationale / Boundary Policy |
|---|---|---|
| `AGENTS.md` | `GIT_REQUIRED` | Core workspace agent operating instructions |
| `README.md` | `GIT_REQUIRED` | Project architecture and directory overview |
| `.gitignore` | `GIT_REQUIRED` | Version control exclusion rules |
| `PROF-TZ-0001_WORKSPACE_BOOTSTRAP.md` | `GIT_REQUIRED` | Approved task specification (historical baseline) |
| `PROF-TZ-0002.md` | `GIT_REQUIRED` | Approved task specification (historical baseline) |
| `PROF-TZ-0003.md` | `GIT_REQUIRED` | Approved task specification (current task) |
| `ROADMAP_PROFF_v1.0.md` | `GIT_REQUIRED` | Approved phase roadmap source |
| `.agents/rules/01-project-boundary.md` | `GIT_REQUIRED` | Workspace rule: boundary enforcement |
| `.agents/rules/02-evidence-and-privacy.md` | `GIT_REQUIRED` | Workspace rule: evidence and privacy |
| `governance/naming.md` | `GIT_REQUIRED` | PGSM taxonomy and naming standard |
| `governance/policies/privacy_boundary.md` | `GIT_REQUIRED` | Privacy, non-clinical, and isolation policy |
| `governance/policies/recovery_policy.md` | `GIT_REQUIRED` | Recovery baseline and restoration policy |
| `inputs/raw_exports/.gitkeep` | `GIT_REQUIRED` | Structural placeholder |
| `inputs/source_staging/.gitkeep` | `GIT_REQUIRED` | Structural placeholder |
| `outputs/README.md` | `GIT_REQUIRED` | Structural documentation |
| `pipeline/README.md` | `GIT_REQUIRED` | Module documentation |
| `project_state/CHANGELOG.md` | `GIT_REQUIRED` | PGSM changelog |
| `project_state/CURRENT_STATE.md` | `GIT_REQUIRED` | Authoritative single source of truth |
| `project_state/DECISIONS.md` | `GIT_REQUIRED` | ADR registry |
| `project_state/ISSUES.md` | `GIT_REQUIRED` | Issues registry |
| `project_state/ROADMAP.md` | `GIT_REQUIRED` | Active project roadmap |
| `project_state/TASK_REGISTER.md` | `GIT_REQUIRED` | Active task register |
| `project_state/history/state/STATE-000001.md` | `GIT_REQUIRED` | Immutable state history snapshot |
| `project_state/history/state/STATE-000002.md` | `GIT_REQUIRED` | Immutable state history snapshot |
| `project_state/history/state/STATE-000003.md` | `GIT_REQUIRED` | Immutable state history snapshot |
| `project_state/history/state/STATE-000004.md` | `GIT_REQUIRED` | Immutable state history snapshot |
| `project_state/history/state/STATE-000005.md` | `GIT_REQUIRED` | Immutable state history snapshot |
| `project_state/structure/STRUCTURE.md` | `GIT_REQUIRED` | Physical directory baseline |
| `project_state/structure/STRUCTURE_CHANGELOG.md` | `GIT_REQUIRED` | Structure version changelog |
| `project_state/structure/versions/v1.0.0.md` | `GIT_REQUIRED` | Immutable structure snapshot |
| `project_state/structure/versions/v1.1.0.md` | `GIT_REQUIRED` | Immutable structure snapshot |
| `project_state/tasks/TZ-0001-workspace-bootstrap/**` | `GIT_REQUIRED` | Completed task artifacts (`TZ.md`, `WALKTHROUGH.md`) |
| `project_state/tasks/TZ-0002-environment-audit/TZ.md` | `GIT_REQUIRED` | Task specification |
| `project_state/tasks/TZ-0002-environment-audit/DISCOVERY.md` | `GIT_REQUIRED` | Task discovery evidence |
| `project_state/tasks/TZ-0002-environment-audit/CUSTOMIZATION_INVENTORY.md` | `GIT_REQUIRED` | Audit inventory |
| `project_state/tasks/TZ-0002-environment-audit/CONFLICT_MATRIX.md` | `GIT_REQUIRED` | Conflict matrix |
| `project_state/tasks/TZ-0002-environment-audit/R0_MANIFEST.json` | `GIT_REQUIRED` | Cryptographic baseline manifest |
| `project_state/tasks/TZ-0002-environment-audit/VALIDATION.md` | `GIT_REQUIRED` | Validation evidence |
| `project_state/tasks/TZ-0002-environment-audit/WALKTHROUGH.md` | `GIT_REQUIRED` | Task walkthrough |
| `project_state/tasks/TZ-0002-environment-audit/R0_BACKUP.zip` | `GIT_EXCLUDED` | Local binary backup archive; excluded from VCS |
| `project_state/tasks/TZ-0003-isolated-git-checkpoints/**` | `GIT_REQUIRED` | Task artifacts for current task |
| `specifications/knowledge_base/README.md` | `GIT_REQUIRED` | Scientific KB status documentation |
| `tests/README.md` | `GIT_REQUIRED` | Testing documentation |
| `tg_save/**` | `GIT_EXCLUDED` | Personal Telegram export (messages, audio, media, stickers, json) |
| `inputs/raw_exports/**` (except `.gitkeep`) | `GIT_EXCLUDED` | Raw case ingestion payloads |
| `inputs/source_staging/**` (except `.gitkeep`) | `GIT_EXCLUDED` | Staged external documents |
| `outputs/**` (except `README.md`) | `GIT_EXCLUDED` | Generated profiling outputs and passports |
| `*.zip`, `*.tar`, `*.gz` | `GIT_EXCLUDED` | Archive files |
| `.env`, `.env.*` (except `.env.example`) | `GIT_EXCLUDED` | Secrets and environment configurations |
| `.venv/`, `venv/`, `__pycache__/` | `GIT_EXCLUDED` | Virtual environments and compiler caches |
| `_tmp_*` | `GIT_EXCLUDED` | Temporary validation folders |
