# PsychoPassport Engine — Project Roadmap v1.0

**Status:** ACTIVE  
**Verified Root:** `C:\Users\candy\Desktop\lil_projects\proff` (Verified: EXISTING, not a link/junction)  
**Governance:** PGSM v1.0.0  
**Current Structure Version:** v1.2.0  
**Knowledge-Base Release:** Grok v1.1.0 (`IMPORT_PENDING`)  

---

## 1. Scope & Boundaries

The future engine ingests authorized text, audio, video, images, and documents; preserves originals and provenance; transcribes audio/video; extracts attributable observations; audits consistency and communicative patterns; produces evidence-grounded communication reports with unknowns and human review.

It does not diagnose mental illness, infer deceit from face/voice, or classify sensitive personal traits from unconsented data. No third-party upload, GitHub push, or cloud LLM use is authorized by this roadmap.

---

## 2. Phases and Gates

| Phase | Delivery | Technical Task(s) | Status | Exit Gate |
|---|---|---|---|---|
| **PH-01** | Workspace discovery and non-destructive PGSM bootstrap | PROF-TZ-0001 | **COMPLETED** | Exact root verified; existing files preserved; actual tree, state, task log, `.gitignore` and evidence created; no global modifications |
| **PH-02** | Local customization inventory, scoped rules, recovery policy | PROF-TZ-0002 | **COMPLETED** | Full inventory of rules/skills/agents/plugins/MCP/hooks; permissions/dependency assessment; R0 backup/restore verified; workspace rules established |
| **PH-03** | Isolated Git and optional private GitHub checkpoints | PROF-TZ-0003 | **COMPLETED** | Independent local Git initialized; secrets/PII excluded; native ignore tests pass; local checkpoint verified; remote PUSH_PENDING |
| **PH-04** | Source intake and scientific KB normalization | PROF-TZ-0004-KB | `NOT_STARTED` | Raw source hashes; catalog count reconciled; references verified independently; permissions reviewed; no unlicensed bulk download |
| **PH-05** | Multimodal ingestion and normalization | PROF-TZ-0005 | `NOT_STARTED` | Reproducible accepted-format conversion; text and ASR with timestamps, language, uncertainty, failed-segment statuses; channel isolation |
| **PH-06** | Evidence/analysis contracts and targeted pilot | PROF-TZ-0006 | `NOT_STARTED` | Observation vs inference separation; claim-to-evidence traceability; baseline controls; no fabricated psychometric intervals; negative tests |
| **PH-07** | Report synthesis and human review | PROF-TZ-0007 | `NOT_STARTED` | Schema checks, cross-modal provenance, alternative explanations, neutral defensive responses, redaction and review gate |
| **PH-08** | End-to-end validation, privacy/security, release | PROF-TZ-0008 | `NOT_STARTED` | Approved synthetic/consented test set; quality metrics by channel; failure recovery; deletion/retention policy; verified no-leak tests |

---

## 3. Future Physical Folders (Deferred to Respective Phases)

In accordance with minimal scaffolding rules, the following directories are documented in this roadmap and will be instantiated only during their respective implementation phases:
- `pipeline/ingestion/` (PH-05)
- `pipeline/conversion/` (PH-05)
- `pipeline/transcription/` (PH-05)
- `pipeline/analyzers/` (PH-06)
- `pipeline/synthesis/` (PH-07)
- `inputs/reference_library/` (PH-04)
- `specifications/schemas/` (PH-04)
- `.agents/skills/` (PH-02 / as needed)
- `.agents/agents/` (PH-02 / as needed)
- `outputs/passports/` (PH-07)
- `tests/unit/` (PH-06)

---

## 4. Decisions Required Before Processing Personal Cases

1. Lawful basis / consent of relevant parties and deployment jurisdiction.
2. Allowed recording/media sources and third-party transfer policy.
3. Retention, deletion, backups, access, and encryption rules.
4. Model/API selection and processing mode (local/cloud).
5. Pilot acceptance metrics and human reviewer role.
