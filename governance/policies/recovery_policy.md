# Recovery & Baseline Policy

**Project:** PsychoPassport Engine (`proff`)  
**Standard:** PGSM v1.0.0  
**Effective Date:** 2026-11-12  
**Status:** ENFORCED  

---

## 1. Purpose

This policy governs the creation of recovery baselines, emergency rollback procedures, and state restoration protocols for the PsychoPassport Engine workspace, ensuring non-destructive operations and deterministic state recovery.

---

## 2. Recovery Protocol & Core Contracts

### 2.1 Pre-Change Snapshot Contract
- Prior to any mutation of existing project configuration, governance, or code files, a pre-change baseline snapshot and backup archive must be established.
- The baseline must capture all target file paths, sizes, and cryptographic SHA-256 hashes in an immutable machine-readable manifest (`R0_MANIFEST.json`).

### 2.2 Hash Validation Contract
- Every restore operation must validate restored file contents against the recorded SHA-256 hashes in the manifest.
- A restoration is declared valid (`PASS`) only when 100% of restored files achieve byte-for-byte parity with the manifest.

### 2.3 Allowed Write Paths
- Recovery writes are permitted solely within the canonical project root (`C:\Users\candy\Desktop\lil_projects\proff`).
- Traversal or restoration outside this root is strictly forbidden.

### 2.4 Checkpointing on Interruption
- If an automated process, pipeline task, or file operation is interrupted, corrupted, or aborted, the system must record a checkpoint state indicating `BLOCKED` or `FAILED` in `project_state/CURRENT_STATE.md`.
- No intermediate unverified files may be promoted to authoritative state.

### 2.5 Failure Reporting
- In the event of a validation or restore failure, the failure condition, exact mismatch details, and affected file paths must be logged in `project_state/ISSUES.md` and the corresponding task's `WALKTHROUGH.md`.
- No sensitive or private data may be included in failure logs.

### 2.6 Step-by-Step Restoration Procedure
1. **Freeze State**: Immediately halt all concurrent write operations.
2. **Determine Scope of Mutation**: Run a recursive file inventory and identify modified or extraneous files by comparing current SHA-256 hashes against `R0_MANIFEST.json`.
3. **Isolate Target Workspace**: Ensure no temporary processes are holding file locks on target resources.
4. **Extract Baseline**: Extract verified archive (`R0_BACKUP.zip`) to an isolated staging directory within project root.
5. **Verify Staged Contents**: Compute SHA-256 of all staged files and ensure 100% match with `R0_MANIFEST.json`.
6. **Apply Restore**: Overwrite modified files from the verified staged copy to restore original state. Extraneous uncommitted files must be quarantined or reviewed.
7. **Clean Staging**: Remove temporary staging directory.
8. **Re-Verify Post-Restore**: Recompute SHA-256 across all restored workspace files to confirm baseline integrity.

### 2.7 Human Escalation
- Automated rollback must NOT be initiated blindly without human operator confirmation when file corruption or unexpected data modification occurs.
- If hash parity cannot be restored, the agent must immediately stop, log the anomaly, and escalate to the human project owner.

### 2.8 Post-Restore Validation Gate
- Following restoration, the workspace must undergo complete structural and state verification.
- `project_state/CURRENT_STATE.md` must be updated with the restoration event and reference the validated state revision.

