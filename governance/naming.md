# Naming Conventions & Taxonomy Standard

**Project:** PsychoPassport Engine (`proff`)  
**Standard:** PGSM v1.0.0  

---

## 1. Task Identifiers

- **Format:** `TZ-<NNNN>-<kebab-case-slug>`
- **Example:** `TZ-0001-workspace-bootstrap`
- **Location:** `project_state/tasks/TZ-<NNNN>-<slug>/`
- **Mandatory Files:**
  - `TZ.md`: Exact, immutable specification for the task.
  - `WALKTHROUGH.md`: Factual record of execution, verification commands, and results.

## 2. State & History Records

- **Live State SSOT:** `project_state/CURRENT_STATE.md`
- **Historical Snapshots:** `project_state/history/state/STATE-<NNNNNN>.md` (6-digit monotonic sequence starting at `STATE-000001.md`).

## 3. Structure Versioning

- **Canonical Specification:** `project_state/structure/STRUCTURE.md`
- **Version Snapshots:** `project_state/structure/versions/v<MAJOR>.<MINOR>.<PATCH>.md`
- **Changelog:** `project_state/structure/STRUCTURE_CHANGELOG.md`

## 4. Directory & File Conventions

- **Governance & Indices:** UPPERCASE markdown files in root and `project_state/` (`README.md`, `AGENTS.md`, `CURRENT_STATE.md`, `ROADMAP.md`, `TASK_REGISTER.md`, `ISSUES.md`, `DECISIONS.md`, `CHANGELOG.md`, `STRUCTURE.md`).
- **Directories:** Lowercase `kebab-case` or `snake_case` (e.g., `source_staging`, `raw_exports`, `knowledge_base`).
- **Policies:** Lowercase snake_case in `governance/policies/` (e.g., `privacy_boundary.md`).

