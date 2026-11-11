# Local Git Version Control Policy

**Project:** PsychoPassport Engine (`proff`)  
**Standard:** PGSM v1.0.0  
**Status:** ENFORCED  
**Effective Date:** 2026-11-12  

---

## 1. Repository Ownership

The PsychoPassport Engine Git repository is an independent, project-scoped version control boundary. It manages:
- Project governance, policies, and specifications.
- Project state machine (`project_state/`), roadmap, task records, and immutable history.
- Core source code, algorithms, and modules in `pipeline/`.
- Test suites, fixtures, and synthetic benchmarks in `tests/`.
- Workspace-level agent rules and customization contracts in `.agents/`.

Git is **never** a storage medium for raw personal communications, unconsented biometric audio/video recordings, clinical profiling reports, credentials, or monolithic binary dumps.

---

## 2. Project Boundary

All Git commands and references must operate exclusively within the canonical write root:
`C:\Users\candy\Desktop\lil_projects\proff`

Cross-boundary indexing, symlink escapes, parent directory traversal, and modification of global or ancestral repositories are strictly forbidden.

---

## 3. Pre-Task Git Checks

Before beginning any task that modifies repository state, the executing agent must:
1. Confirm the active Git top-level matches canonical project root (`git rev-parse --show-toplevel`).
2. Verify clean worktree status or establish that changes belong strictly to the registered task (`git status --porcelain`).
3. Verify that the current branch is the approved work branch (`main` by default).

---

## 4. File Classification Contract

Every file candidate must be categorized prior to staging according to `FILE_CLASSIFICATION.md`:
- `GIT_REQUIRED`: Technical code, documentation, governance policies, and keep-files.
- `GIT_EXCLUDED`: Personal chat archives (`tg_save/`), raw media files, local backup archives (`*.zip`), `.env` files, and temporary artifacts.
- `REVIEW_REQUIRED`: Unclassified files requiring explicit manual or automated review before staging.

---

## 5. Secret Scanning Protocol

Prior to creating any Git commit:
1. Staged content must be inspected using automated pattern checks for cryptographic private key blocks (such as PEM header blocks), API access tokens (e.g. GitHub/AIza/cloud API key prefixes), connection strings, and credentials.
2. Staged diffs must be screened to ensure no real personal identifiers, chat text, or audio transcripts are included.
3. If any secret or sensitive personal payload is detected, staging must be halted immediately.

---

## 6. Local Checkpoint Strategy

1. Checkpoints must be task-scoped and correspond directly to registered PGSM tasks (`TZ-XXXX`).
2. Blind staging (`git add -A` or `git add .`) is strictly prohibited. Selective staging (`git add <path>`) must be practiced.
3. Checkpoint commit messages must cite the active Task ID:
   `TZ-XXXX: <imperative summary of changes>`
4. On task completion, a machine-readable receipt (`LOCAL_CHECKPOINT_RECEIPT.json`) recording the commit SHA must be generated.

---

## 7. Remote Authorization Gates

1. By default, the local repository has **zero** remote endpoints (`git remote -v` is empty).
2. Creating an external remote (e.g. on GitHub) or pushing repository state requires **explicit, separate user authorization**.
3. In the absence of explicit permission, remote operations remain in status `PUSH_PENDING`.

---

## 8. Allowed Branches

- **`main`**: The primary authoritative branch representing verified, stable task checkpoints.
- Feature/experimental branches must branch off `main` and be merged only upon passing PGSM validation.

---

## 9. Push and SHA Verification Protocol

When remote push is explicitly authorized:
1. Target remote must be verified as `PRIVATE` visibility.
2. The local `HEAD` commit SHA must be recorded prior to push.
3. Post-push verification must fetch the remote branch ref and confirm identical SHA parity with local `HEAD`.

---

## 10. Failure Recovery Procedures

1. **Commit Interruption**: If a task fails or aborts mid-way, staged changes must remain in index or be unstaged with `git restore --staged <file>`. Destructive working tree resets are prohibited.
2. **Rollback**: Rollbacks must refer to verified checkpoints or `R0_BACKUP.zip` under the protocol defined in `governance/policies/recovery_policy.md`.

---

## 11. Human Approval Gates

Human owner approval is mandatory before:
1. Adding any external Git remote URL.
2. Pushing any branch to an external network.
3. Staging any file categorized as `REVIEW_REQUIRED`.
4. Overwriting or resetting any Git history.

---

## 12. Forbidden Destructive Commands

The following Git commands are strictly prohibited in automated execution:
- `git reset --hard`
- `git clean -fdx`
- `git push --force` or `git push --force-with-lease`
- `git rebase` across published checkpoints
- `git filter-branch` or destructive history rewriting tools
- Force-adding ignored files (`git add -f`)
