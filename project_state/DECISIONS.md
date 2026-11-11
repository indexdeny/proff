# Architectural Decision Records (ADR) Register

**Project:** PsychoPassport Engine (`proff`)  
**Standard:** PGSM v1.0.0  

---

## Decisions Index

| ADR ID | Date | Status | Title | Summary |
|---|---|---|---|---|
| `ADR-0001` | 2026-11-12 | **ACCEPTED** | Bootstrap Workspace Under PGSM v1.0.0 | Adopt PGSM v1.0.0 specification with single live state SSOT (`CURRENT_STATE.md`), monotonic history snapshots, and strict task registration. |
| `ADR-0002` | 2026-11-12 | **ACCEPTED** | Non-Destructive Scaffolding and Personal Data Containment | Preserve pre-existing `tg_save/` without reading or moving; enforce strict exclusion in `.gitignore` and privacy policy. |
| `ADR-0003` | 2026-11-12 | **ACCEPTED** | Independence of Structure Version from KB Release | Decouple physical directory structure version (`v1.0.0` / `v1.1.0`) from future Grok knowledge base release version (`1.1.0`). |
| `ADR-0004` | 2026-11-12 | **ACCEPTED** | Workspace-Scoped Rules via `.agents/rules/` | Instantiate `.agents/rules/` for fine-grained workspace enforcement (`01-project-boundary.md`, `02-evidence-and-privacy.md`), advancing structure version to `v1.1.0`. |
| `ADR-0005` | 2026-11-12 | **ACCEPTED** | Recovery Baseline R0 and Policy Formalization | Establish `R0_MANIFEST.json` and `R0_BACKUP.zip` with verified restore test; codify `governance/policies/recovery_policy.md` before Git initialization. |
