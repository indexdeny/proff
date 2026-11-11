# Structure Changelog

All changes to the physical directory structure of `proff` are tracked in this file.

---

## [1.2.0] - 2026-11-12

### Added
- Initialized independent local Git repository (`.git/`) scoped to `C:\Users\candy\Desktop\lil_projects\proff`.
- Created `project_state/decisions/` directory for standalone Architectural Decision Record documents.
- Added `project_state/decisions/ADR-0006-git-isolation.md`.
- Added `governance/git_policy.md` and `.agents/rules/03-git-checkpoints.md`.
- Established task directory `project_state/tasks/TZ-0003-isolated-git-checkpoints/`.
- Created immutable snapshot [`versions/v1.2.0.md`](versions/v1.2.0.md).

---

## [1.1.0] - 2026-11-12

### Added
- Created `.agents/rules/` for workspace-scoped execution rules:
  - `01-project-boundary.md`
  - `02-evidence-and-privacy.md`
- Created `governance/policies/recovery_policy.md` defining R0 recovery protocols.
- Established task directory `project_state/tasks/TZ-0002-environment-audit/`.
- Created immutable snapshot [`versions/v1.1.0.md`](versions/v1.1.0.md).

---

## [1.0.0] - 2026-11-12

### Initialized
- Initial minimal physical scaffold approved and established under `TZ-0001-workspace-bootstrap`.
- Defined baseline directory tree across `governance/`, `project_state/`, `inputs/`, `specifications/`, `pipeline/`, `outputs/`, and `tests/`.
- Created immutable specification [`versions/v1.0.0.md`](versions/v1.0.0.md).
