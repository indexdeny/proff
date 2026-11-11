# Workspace Rule: Evidence Grounding & Data Privacy

**Scope:** `C:\Users\candy\Desktop\lil_projects\proff` and all subdirectories  
**Enforcement:** Mandatory / Always-On  

---

## 1. Data Containment & Personal Data Protection

1. **Strict Local Isolation**: Case communication archives (such as `tg_save/`), audio/video recordings, biometric voice data, and extracted transcripts must remain strictly local. No transmission to external network endpoints, third-party cloud services, or unauthorized models is permitted.
2. **Zero-Tracking Invariant**: Raw exports, case payloads, and personal communication archives must never be staged, tracked, or committed to Git.
3. **No Hidden Export**: Telemetry, logs, task walkthroughs, and error diagnostics must strictly redact all personal identifying information (PII), logging only relative paths and cryptographic hashes.

## 2. Evidence Grounding & Non-Clinical Invariants

1. **Observation vs. Inference**: All analytical statements must maintain rigorous separation between direct, verifiable acoustic/textual observations and derived interpretative hypotheses.
2. **Provenance & Traceability**: Every analytical assertion must link directly to observable evidence timestamps, quotes, or metric offsets.
3. **Insufficient Evidence**: When evidence is ambiguous, incomplete, or insufficient, the engine must return explicit insufficient-evidence classifications (`UNKNOWN` / `INSUFFICIENT_DATA`), never speculating or fabricating psychometric intervals.
4. **No Clinical Psychiatric Diagnoses**: The system is an observational communication pattern tool. Generating clinical psychiatric diagnoses, mental pathology labels, or unverified claims of deceit is strictly forbidden.

