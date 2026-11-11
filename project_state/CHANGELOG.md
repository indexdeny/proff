# Changelog

All notable changes to the PsychoPassport Engine (`proff`) workspace will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [PGSM v1.0.0](PGSM_PROJECT_STANDARD_v1.0.0.md).

---

## [1.1.0] - 2026-11-12

### Added
- Executed task `TZ-0002-environment-audit`:
  - Conducted full read-only audit across Rules, Skills, Plugins, MCP servers, Agents, and Hooks.
  - Generated `CUSTOMIZATION_INVENTORY.md` covering 101 skills, 3 plugins, 4 MCP servers, and active rules.
  - Formulated `CONFLICT_MATRIX.md` with conflict classifications and recommendations.
  - Constructed verified baseline `R0_MANIFEST.json` and `R0_BACKUP.zip` (54,947 bytes, 29 files, 100% restore parity).
  - Codified `governance/policies/recovery_policy.md`.
  - Instantiated `.agents/rules/` with `01-project-boundary.md` and `02-evidence-and-privacy.md`.
  - Elevated workspace structure version to `v1.1.0` and recorded immutable snapshot `versions/v1.1.0.md`.
  - Updated `.gitignore` to explicitly exclude backup archives (`*.zip`, `*_BACKUP.zip`).

---

## [1.0.0] - 2026-11-12

### Added
- Executed task `TZ-0001-workspace-bootstrap`:
  - Verified canonical root boundary `C:\Users\candy\Desktop\lil_projects\proff` (not a link/reparse point).
  - Preserved pre-existing files (`PROF-TZ-0001_WORKSPACE_BOOTSTRAP.md`, `ROADMAP_PROFF_v1.0.md`) and directory `tg_save/`.
  - Created minimal physical directory tree (`governance/`, `project_state/`, `inputs/`, `specifications/`, `pipeline/`, `outputs/`, `tests/`).
  - Added privacy-first `.gitignore` excluding secrets, `.env`, audio/video files, and raw exports.
  - Established PGSM live state machine (`CURRENT_STATE.md`), roadmap, task register, issues and decisions registers.
  - Created initial and final immutable state snapshots (`STATE-000001.md`, `STATE-000002.md`).
  - Created structure specification `v1.0.0` and changelog.
  - Copied immutable task specification to `project_state/tasks/TZ-0001-workspace-bootstrap/TZ.md`.
