# Physical Directory Structure

**Current Structure Version:** `v1.2.0`  
**Authoritative Version Snapshot:** [`versions/v1.2.0.md`](versions/v1.2.0.md)  
**Last Updated:** 2026-11-12  

---

## Active Structure Inventory

| Path | Type | Purpose / Description |
|---|---|---|
| `.git/` | Directory | Local independent Git repository boundary |
| `AGENTS.md` | File | Workspace-level agent instructions, startup order, and invariants |
| `README.md` | File | Project overview and architecture description |
| `.gitignore` | File | Strict exclusion rules for secrets, caches, media, and case exports |
| `.agents/` | Directory | Workspace agent configuration directory |
| `.agents/rules/` | Directory | Workspace-scoped agent enforcement rules |
| `.agents/rules/01-project-boundary.md` | File | Boundary lockdown and anti-traversal rule |
| `.agents/rules/02-evidence-and-privacy.md` | File | Evidence grounding, privacy, and non-clinical rule |
| `.agents/rules/03-git-checkpoints.md` | File | Git version control and checkpoint verification rule |
| `governance/` | Directory | Project policies, privacy boundaries, and naming standards |
| `governance/git_policy.md` | File | Local Git version control policy |
| `governance/policies/privacy_boundary.md` | File | Enforced privacy, non-clinical, and isolation policy |
| `governance/policies/recovery_policy.md` | File | Baseline creation, verification, and recovery protocols |
| `governance/naming.md` | File | PGSM naming conventions and taxonomy standard |
| `project_state/` | Directory | Canonical state, roadmap, tasks, and history |
| `project_state/CURRENT_STATE.md` | File | Authoritative single source of truth for live project state |
| `project_state/ROADMAP.md` | File | Phase progression and technical gates plan |
| `project_state/TASK_REGISTER.md` | File | Monotonic index of registered tasks |
| `project_state/ISSUES.md` | File | Tracked workspace issues and mitigations |
| `project_state/DECISIONS.md` | File | Architectural decision records index |
| `project_state/CHANGELOG.md` | File | Project modification history |
| `project_state/decisions/` | Directory | Standalone Architectural Decision Record documents |
| `project_state/decisions/ADR-0006-git-isolation.md` | File | Architectural decision on isolated Git repository |
| `project_state/tasks/` | Directory | Task specifications and execution walkthroughs |
| `project_state/tasks/TZ-0001-workspace-bootstrap/` | Directory | Task directory for workspace bootstrap |
| `project_state/tasks/TZ-0001-workspace-bootstrap/TZ.md` | File | Exact task specification for TZ-0001 |
| `project_state/tasks/TZ-0001-workspace-bootstrap/WALKTHROUGH.md` | File | Detailed execution log and validation results |
| `project_state/tasks/TZ-0002-environment-audit/` | Directory | Task directory for environment audit |
| `project_state/tasks/TZ-0002-environment-audit/TZ.md` | File | Exact task specification for TZ-0002 |
| `project_state/tasks/TZ-0002-environment-audit/DISCOVERY.md` | File | Preflight discovery log for TZ-0002 |
| `project_state/tasks/TZ-0002-environment-audit/CUSTOMIZATION_INVENTORY.md` | File | Complete environment customization inventory |
| `project_state/tasks/TZ-0002-environment-audit/CONFLICT_MATRIX.md` | File | Conflict analysis and recommendations matrix |
| `project_state/tasks/TZ-0002-environment-audit/R0_MANIFEST.json` | File | Cryptographic baseline manifest |
| `project_state/tasks/TZ-0002-environment-audit/VALIDATION.md` | File | Automated validation checks evidence |
| `project_state/tasks/TZ-0002-environment-audit/WALKTHROUGH.md` | File | Detailed execution walkthrough and DOD matrix |
| `project_state/tasks/TZ-0003-isolated-git-checkpoints/` | Directory | Task directory for isolated Git checkpoints |
| `project_state/tasks/TZ-0003-isolated-git-checkpoints/TZ.md` | File | Exact task specification for TZ-0003 |
| `project_state/tasks/TZ-0003-isolated-git-checkpoints/DISCOVERY.md` | File | Preflight discovery log for TZ-0003 |
| `project_state/tasks/TZ-0003-isolated-git-checkpoints/R0_INTEGRITY_REPORT.md` | File | Verification of R0 baseline integrity |
| `project_state/tasks/TZ-0003-isolated-git-checkpoints/FILE_CLASSIFICATION.md` | File | File classification manifest for Git tracking |
| `project_state/tasks/TZ-0003-isolated-git-checkpoints/GITHUB_READINESS.md` | File | GitHub readiness and remote posture report |
| `project_state/tasks/TZ-0003-isolated-git-checkpoints/LOCAL_CHECKPOINT_RECEIPT.json` | File | Cryptographic receipt for local Git checkpoint |
| `project_state/tasks/TZ-0003-isolated-git-checkpoints/VALIDATION.md` | File | Automated validation checks evidence |
| `project_state/tasks/TZ-0003-isolated-git-checkpoints/WALKTHROUGH.md` | File | Detailed execution walkthrough and DOD matrix |
| `project_state/structure/` | Directory | Physical structure governance and history |
| `project_state/structure/STRUCTURE.md` | File | This inventory file |
| `project_state/structure/STRUCTURE_CHANGELOG.md` | File | Changelog of physical structure evolutions |
| `project_state/structure/versions/` | Directory | Immutable version specifications |
| `project_state/structure/versions/v1.0.0.md` | File | Immutable specification of v1.0.0 |
| `project_state/structure/versions/v1.1.0.md` | File | Immutable specification of v1.1.0 |
| `project_state/structure/versions/v1.2.0.md` | File | Immutable specification of v1.2.0 |
| `project_state/history/` | Directory | Immutable historical state records |
| `project_state/history/state/` | Directory | Sequence of immutable state snapshots |
| `project_state/history/state/STATE-000001.md` | File | State snapshot (Rev 1, TZ-0001 In-Progress) |
| `project_state/history/state/STATE-000002.md` | File | State snapshot (Rev 2, TZ-0001 Completed) |
| `project_state/history/state/STATE-000003.md` | File | State snapshot (Rev 3, TZ-0002 In-Progress) |
| `project_state/history/state/STATE-000004.md` | File | State snapshot (Rev 4, TZ-0002 Completed) |
| `project_state/history/state/STATE-000005.md` | File | State snapshot (Rev 5, TZ-0003 In-Progress) |
| `project_state/history/state/STATE-000006.md` | File | State snapshot (Rev 6, TZ-0003 Completed) |
| `inputs/` | Directory | Intake directories for data and staging |
| `inputs/source_staging/` | Directory | Staging area for validated source documents |
| `inputs/source_staging/.gitkeep` | File | Keep placeholder (contents ignored by Git) |
| `inputs/raw_exports/` | Directory | Raw case exports intake (strictly git-ignored) |
| `inputs/raw_exports/.gitkeep` | File | Keep placeholder (contents ignored by Git) |
| `specifications/` | Directory | Canonical specifications and schemas |
| `specifications/knowledge_base/` | Directory | Knowledge-base specification intake |
| `specifications/knowledge_base/README.md` | File | Status of scientific KB (IMPORT_PENDING) |
| `pipeline/` | Directory | Processing modules container |
| `pipeline/README.md` | File | Documentation of future pipeline modules |
| `outputs/` | Directory | Generated analytical reports and passports |
| `outputs/README.md` | File | Documentation of output artifacts (git-ignored) |
| `tests/` | Directory | Test suites and benchmarks container |
| `tests/README.md` | File | Documentation of planned test suites |
