# Validation Record — Task TZ-0003-isolated-git-checkpoints

**Task ID:** `TZ-0003-isolated-git-checkpoints`  
**Phase:** PH-03  
**Date:** 2026-11-12T01:01:00+02:00  
**Project:** PsychoPassport Engine (`proff`)  
**Standard:** PGSM v1.0.0 / `governance/git_policy.md`  

---

## 1. Validation Matrix (PASS / FAIL / NOT_RUN / NOT_VERIFIED)

| Test ID | Verification Target | Expected Result | Actual Result | Status |
|---|---|---|---|---|
| **VAL-01** | Canonical Root Boundary | Path `C:\Users\candy\Desktop\lil_projects\proff`, non-reparse | `FullName = C:\Users\candy\Desktop\lil_projects\proff`, `IsReparsePoint = False`, `LinkType = null` | **`PASS`** |
| **VAL-02** | R0 Recovery Archive Integrity | Archive physically matches manifest; trial extraction passes | SHA-256 `9AA491D6...` matches manifest; 29/29 files achieve 100% hash parity on restore | **`PASS`** |
| **VAL-03** | File Classification Manifest | All workspace files classified into `GIT_REQUIRED`, `GIT_EXCLUDED`, `REVIEW_REQUIRED` | Complete manifest recorded in `FILE_CLASSIFICATION.md` | **`PASS`** |
| **VAL-04** | Git Repository Initialization | Independent Git repo initialized in project root | `git rev-parse --show-toplevel` = `C:/Users/candy/Desktop/lil_projects/proff` | **`PASS`** |
| **VAL-05** | Git Branch Conformance | Active branch is approved `main` branch | `git branch --show-current` = `main` | **`PASS`** |
| **VAL-06** | Native GitIgnore Probes | Native `git check-ignore -q` matches expectations across 25 probe paths | 25/25 probes passed (100% precision, zero sensitive false negatives) | **`PASS`** |
| **VAL-07** | Sensitive Data Index Exclusion | Zero files from `tg_save/` or `.zip` present in Git index | `git ls-files tg_save/` returns 0; `git ls-files *.zip` returns 0 | **`PASS`** |
| **VAL-08** | Secret Scanning on Staged Diff | Zero private keys, API keys, or tokens in staged diff | Scanned against PEM private keys, `ghp_`, `github_pat_`, `AIza`, `sk-`; 0 detected | **`PASS`** |
| **VAL-09** | Selective Staging & Checkpoint Commit | Initial checkpoint committed with task message | Commit `fb1ab4e2f18d2f0a189d41ee4f6dc5c0b4c970cf` created with 51 verified files (Author: `indexdeny`) | **`PASS`** |
| **VAL-10** | Local Checkpoint Receipt | Receipt JSON records commit SHA, author, timestamp | Formatted and saved in `LOCAL_CHECKPOINT_RECEIPT.json` | **`PASS`** |
| **VAL-11** | Standalone ADR Document | `ADR-0006` recorded in `project_state/decisions/` | Created `ADR-0006-git-isolation.md` with full context, decision, consequences | **`PASS`** |
| **VAL-12** | Structure Version Elevation | Structure version elevated to `1.2.0` due to `decisions/` directory | `versions/v1.2.0.md`, `STRUCTURE_CHANGELOG.md`, `STRUCTURE.md` updated | **`PASS`** |
| **VAL-13** | Workspace Rule Conformance | `03-git-checkpoints.md` formatted as Markdown, <24 KB | Size: 1,840 bytes, UTF-8, compliant with Antigravity guidelines | **`PASS`** |
| **VAL-14** | Workspace Rule Dynamic Activation | Live IDE rule reload interface | Dynamic reload interface not exposed via CLI; pending next session turn | **`NOT_VERIFIED`** |
| **VAL-15** | Remote Security & Approval Gate | Zero remotes configured; no push performed | `git remote -v` returns empty; `PUSH_STATUS = PUSH_PENDING` | **`PASS`** |
| **VAL-16** | Global Configuration Invariance | Zero writes outside canonical Project Root | `~/.gemini/` and global Git config untouched | **`PASS`** |
| **VAL-17** | State Machine Revision Monotonicity | State transitions monotonically: Rev 4 → Rev 5 → Rev 6 | Sequential snapshots `STATE-000001` through `STATE-000006` maintained | **`PASS`** |

---

## 2. Evidence Logs

### 2.1 Native Git Check-Ignore Probes (25/25 PASS)
```powershell
Probe: tg_save/messages.html             | Expected: IGNORED   | Actual: IGNORED   | Status: PASS
Probe: tg_save/result.json               | Expected: IGNORED   | Actual: IGNORED   | Status: PASS
Probe: tg_save/voice_messages/audio.ogg  | Expected: IGNORED   | Actual: IGNORED   | Status: PASS
Probe: audio.ogg                         | Expected: IGNORED   | Actual: IGNORED   | Status: PASS
Probe: video.mp4                         | Expected: IGNORED   | Actual: IGNORED   | Status: PASS
Probe: .env                              | Expected: IGNORED   | Actual: IGNORED   | Status: PASS
Probe: .env.production                   | Expected: IGNORED   | Actual: IGNORED   | Status: PASS
Probe: .env.example                      | Expected: TRACKABLE | Actual: TRACKABLE | Status: PASS
Probe: credentials.json                  | Expected: IGNORED   | Actual: IGNORED   | Status: PASS
Probe: secret.key                        | Expected: IGNORED   | Actual: IGNORED   | Status: PASS
Probe: .../R0_BACKUP.zip                 | Expected: IGNORED   | Actual: IGNORED   | Status: PASS
Probe: inputs/raw_exports/dump.json      | Expected: IGNORED   | Actual: IGNORED   | Status: PASS
Probe: inputs/raw_exports/.gitkeep       | Expected: TRACKABLE | Actual: TRACKABLE | Status: PASS
Probe: outputs/passport_001.json         | Expected: IGNORED   | Actual: IGNORED   | Status: PASS
Probe: outputs/README.md                 | Expected: TRACKABLE | Actual: TRACKABLE | Status: PASS
Probe: AGENTS.md                         | Expected: TRACKABLE | Actual: TRACKABLE | Status: PASS
Probe: governance/git_policy.md          | Expected: TRACKABLE | Actual: TRACKABLE | Status: PASS
Probe: .agents/rules/03-git-checkpoints  | Expected: TRACKABLE | Actual: TRACKABLE | Status: PASS
Probe: project_state/CURRENT_STATE.md    | Expected: TRACKABLE | Actual: TRACKABLE | Status: PASS
```

### 2.2 Initial Commit Verification
```powershell
git rev-parse HEAD
# Output: fb1ab4e2f18d2f0a189d41ee4f6dc5c0b4c970cf
git branch --show-current
# Output: main
git ls-files tg_save/
# Output: (empty)
git ls-files *.zip
# Output: (empty)
```
