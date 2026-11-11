# Workspace Rule: Git Version Control & Checkpoint Verification

**Scope:** `C:\Users\candy\Desktop\lil_projects\proff` and all subdirectories  
**Enforcement:** Mandatory / Always-On  

---

## 1. Pre-Operation Verification

1. **Boundary Confinement**: Before performing any Git operation, verify that `git rev-parse --show-toplevel` resolves precisely to `C:\Users\candy\Desktop\lil_projects\proff`. Operating on ancestor or nested repositories is forbidden.
2. **Selective Staging**: Never execute blanket staging (`git add -A` or `git add .`). All staged files must be explicitly specified and validated against `FILE_CLASSIFICATION.md`.

## 2. Security & Data Protection Invariants

1. **Zero Personal Data Staging**: Raw case exports (such as `tg_save/`), audio/video recordings, transcripts, and personal communication data must never be staged or committed.
2. **Secret Screening**: Scan all staged diffs for API keys, private keys, authentication tokens, and credentials prior to committing. If detected, abort commit immediately.
3. **Backup Isolation**: Local backup archives (`*.zip`) and temporary extraction folders must remain git-ignored and never committed.

## 3. Checkpoint Execution & Remote Gates

1. **Task-Specific Commit**: Every commit message must reference the active PGSM Task ID (e.g. `TZ-0003: initialize isolated proff repository`).
2. **Receipt Generation**: Each completed task checkpoint must record its commit SHA in `LOCAL_CHECKPOINT_RECEIPT.json`.
3. **Remote Gate**: In the absence of explicit, separate human authorization, all remote operations remain `PUSH_PENDING`. Remote push and remote creation are prohibited without explicit consent.
4. **Destructive Commands Prohibited**: Do not execute `git reset --hard`, `git push --force`, `git clean -fdx`, or destructive history rewriting.
