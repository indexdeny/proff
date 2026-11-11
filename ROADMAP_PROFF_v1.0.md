# PsychoPassport Engine — Project Roadmap v1.0

Status: PROPOSED; not evidence of execution.
Target candidate root: `C:\Users\candy\Desktop\lil_projects\proff` (from Grok technical specification; verify locally).
Governance: PGSM v1.0.0. Knowledge-base release: Grok v1.1.0, distinct from workspace structure version.

## Scope and boundaries

The future engine ingests authorized text, audio, video, images, and documents; preserves originals and provenance; transcribes audio/video; extracts attributable observations; audits consistency and communicative patterns; produces evidence-grounded communication reports with unknowns and human review. It does not diagnose mental illness, infer deceit from face/voice, or classify sensitive personal traits from unconsented data. No third-party upload, GitHub push, or cloud LLM use is authorized by this roadmap.

## Phases and gates

| Phase | Delivery | Technical task(s) | Exit gate |
|---|---|---|---|
| PH-01 | Workspace discovery and non-destructive PGSM bootstrap | PROF-TZ-0001 | Exact root verified; existing files preserved; actual tree, state, task log, `.gitignore` and evidence created; no global modifications |
| PH-02 | Local customization inventory, scoped rules, recovery policy | PROF-TZ-0002 | Full inventory of rules/skills/agents/plugins/MCP/hooks; permissions/dependency assessment; only authorized local changes; rollback verified |
| PH-03 | Isolated Git and optional private GitHub checkpoints | PROF-TZ-0003 | No inherited Git mutation; secrets/PII excluded; private remote only after explicit permission; SHA parity or PUSH_PENDING |
| PH-04 | Source intake and scientific KB normalization | PROF-TZ-0004-KB (new scope) | Raw source hashes; catalog count reconciled; references verified independently; permissions reviewed; no unlicensed bulk download |
| PH-05 | Multimodal ingestion and normalization | PROF-TZ-0005 | Reproducible accepted-format conversion; text and ASR with timestamps, language, uncertainty, failed-segment statuses; channel isolation |
| PH-06 | Evidence/analysis contracts and targeted pilot | PROF-TZ-0006 | Observation vs inference separation; claim-to-evidence traceability; baseline controls; no fabricated psychometric intervals; negative tests |
| PH-07 | Report synthesis and human review | PROF-TZ-0007 | Schema checks, cross-modal provenance, alternative explanations, neutral defensive responses, redaction and review gate |
| PH-08 | End-to-end validation, privacy/security, release | PROF-TZ-0008 | Approved synthetic/consented test set; quality metrics by channel; failure recovery; deletion/retention policy; verified no-leak tests |

Existing `PROF-TZ-0004_PROFILING_AGENT.md` remains a source proposal; its agent pilot should be scheduled after PH-04 and PH-05 dependencies, rather than silently declared completed.

## Priority sequence

1. Verify root and inventory; bootstrap only minimal directories and PGSM; no dependencies or data downloads.
2. Audit local and inherited Antigravity customizations; do not disable global components without approval.
3. Establish reliable, private version history and recovery checkpoints.
4. Import verified source material using original bytes/hashes; reconcile known catalog-count discrepancy (78 YAML records vs claims of 62).
5. Implement multimodal conversion and transcription with source offsets and channel isolation.
6. Build the evidence and analytical model with explicit insufficient-evidence outcomes and human review.
7. Validate on consented or synthetic cases before any real deployment.

## Decisions required before processing personal cases

- Lawful basis / consent of relevant parties and deployment jurisdiction.
- Allowed recording/media sources and third-party transfer policy.
- Retention, deletion, backups, access, and encryption rules.
- Model/API selection and processing mode (local/cloud).
- Pilot acceptance metrics and human reviewer role.

## Source record

Based on `PGSM_PROJECT_STANDARD_v1.0.0.md`, `00_MASTER_HANDOFF.md`, `antigravity_ide_pgsm_v1_1_0.md`, `PROF-TZ-0002_CUSTOMIZATIONS.md`, `PROF-TZ-0003_GITHUB.md`, `PROF-TZ-0004_PROFILING_AGENT.md`, the Grok KB records (`00_USER_INSTRUCTION.md` through `07_MULTIMODAL_CALIBRATION_AND_PGSM_STATE.md`), `CURRENT_STATE.md`, `WALKTHROUGH.md`, `project_memory.md`, and `ТЗ-Generator-v2.2.txt`. Existing sources are candidates, not executed implementation evidence.
