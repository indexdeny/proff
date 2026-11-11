# ADR-0006: Isolated Local Git Repository & Checkpoint Verification

**Status:** ACCEPTED  
**Date:** 2026-11-12  
**Task ID:** `TZ-0003-isolated-git-checkpoints`  
**Phase:** PH-03  
**Deciders:** Project Owner (`candy`), Antigravity Agent  
**Governance:** PGSM v1.0.0  

---

## 1. Context

The PsychoPassport Engine (`proff`) workspace holds sensitive observational data (personal Telegram exports in `tg_save/`), formal governance policies, and PGSM state machine history. Prior to Phase 3 (`PH-03`), the workspace operated without a version control repository (`NO_GIT_REPOSITORY`). Moving into multimodal pipeline development requires structured source code versioning, reproducible checkpoints, and change traceability without compromising the strict local privacy boundary.

## 2. Problem Statement

How to establish version control for the project while ensuring:
1. Complete isolation from inherited/parent Git repositories.
2. Absolute containment of pre-existing private communications (`tg_save/`) and future raw media.
3. Prevention of unauthorized remote repository creation or code pushes to public/third-party clouds.
4. Deterministic checkpointing aligned with PGSM task states.

## 3. Considered Alternatives

- **Alternative 1: Monolithic Parent Repository** — Track `proff` as a subdirectory of a wider desktop or parent Git repository.  
  *Rejected*: Violates the Project Boundary invariant, leaks unrelated workspace commits, and risks accidental exposure of sensitive case files across projects.
- **Alternative 2: Immediate GitHub Push with Secret Scanning** — Initialize Git and push immediately to a public or private GitHub remote.  
  *Rejected*: Violates the explicit user consent requirement for remote network operations and risks unverified data transmission.
- **Alternative 3: Local Isolated Git Repository with Strict Gates (Chosen)** — Initialize an independent, local-only repository confined strictly to `C:\Users\candy\Desktop\lil_projects\proff`, hardened by native `.gitignore` filtering, secret scanning, selective staging, and an explicit human approval gate for remotes.

## 4. Decision

1. Initialize an independent Git repository directly inside `C:\Users\candy\Desktop\lil_projects\proff` with default branch `main`.
2. Enforce selective staging (`git add <file>`), completely prohibiting blanket staging (`git add -A`).
3. Enforce strict exclusion of `tg_save/`, raw exports, media files, and local backup archives (`*.zip`) in `.gitignore`.
4. Codify the protocol in `governance/git_policy.md` and enforce it via workspace rule `.agents/rules/03-git-checkpoints.md`.
5. Require explicit human authorization prior to adding any remote or executing any push. In the absence of remote authorization, maintain the status as `PUSH_PENDING`.

## 5. Consequences & Architectural Impact

### Positive
- Independent commit history strictly scoped to PsychoPassport Engine.
- Cryptographically verifiable checkpoints linked to PGSM Task IDs.
- Deterministic verification through native `git check-ignore` and diff review.
- Safe rollback point without dependency on external networks.

### Negative / Trade-offs
- Remote synchronization is deferred (`PUSH_PENDING`) until user explicitly authorizes a private GitHub target.
- Requires manual staging discipline rather than automated bulk commits.

## 6. Security Impact

- Eliminates accidental credential and private chat exposure to version control.
- Prevents remote data leakage by disabling network operations by default.
- Guarantees zero tracking of `tg_save/` and backup archives.

## 7. Recovery Implications

- Every completed task produces a discrete Git commit SHA recorded in `LOCAL_CHECKPOINT_RECEIPT.json`.
- State rollback can be performed safely to specific commit points or to baseline `R0_BACKUP.zip`.

## 8. Approval References

- `PROF-TZ-0003_GITHUB.md` / `PROF-TZ-0003.md` (Approved specification for Phase 3).
- `governance/policies/privacy_boundary.md` (Data isolation policy).
- `governance/policies/recovery_policy.md` (Baseline recovery policy).
