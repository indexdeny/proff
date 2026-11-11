# Issues Register

**Project:** PsychoPassport Engine (`proff`)  
**Standard:** PGSM v1.0.0  

---

## Active & Tracked Issues

| Issue ID | Severity | Status | Opened | Description | Mitigation / Resolution |
|---|---|---|---|---|---|
| `ISSUE-0001` | LOW | **MITIGATED** | 2026-11-12 | Pre-existing personal Telegram chat export (`tg_save/`) present in workspace root. | Directory explicitly excluded via `.gitignore` and isolated under `governance/policies/privacy_boundary.md`. Confirmed untracked via `git check-ignore` and absent from `git ls-files`. |
| `ISSUE-0002` | MEDIUM | **TRACKED** | 2026-11-12 | Grok knowledge-base source files (`00_USER_INSTRUCTION.md` through `07_...`) absent from local root. | Marked `IMPORT_PENDING` in `specifications/knowledge_base/README.md`. Intake scheduled for Phase 4 (`PROF-TZ-0004-KB`) with hash validation. |
| `ISSUE-0003` | LOW | **RESOLVED** | 2026-11-12 | No Git repository detected in root or ancestor directories. | Resolved under Task `TZ-0003`: independent Git repository initialized in project root on branch `main` with verified local checkpoint commit `fb1ab4e`. |
| `ISSUE-0004` | MEDIUM | **TRACKED** | 2026-11-12 | 20 GCP/data skills are duplicated identically between `~/.gemini/config/skills/` and `data-agent-kit-plugin/skills/`. | Documented in `CONFLICT_MATRIX.md` as `EXACT_DUPLICATE`. Recommended `REMOVE_AFTER_APPROVAL` pending explicit user authorization. |
| `ISSUE-0005` | LOW | **MITIGATED** | 2026-11-12 | Dynamic in-memory rule reload for newly created `.agents/rules/` cannot be triggered via CLI. | Verified static Markdown syntax, size (<24 KB limit), and file encoding. Dynamic ingestion occurs on subsequent conversation turns. |
| `ISSUE-0006` | LOW | **TRACKED** | 2026-11-12 | Documentation gap: standalone markdown files for historical ADR-0001 through ADR-0005 do not exist. | Recorded in `DECISIONS.md`. In accordance with Invariants, historical records are preserved without fictitious reconstruction. Standalone files instantiated starting with `ADR-0006-git-isolation.md`. |
