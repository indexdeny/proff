# PsychoPassport Engine (`proff`)

## Overview

PsychoPassport Engine (`proff`) is a privacy-first, evidence-grounded communication pattern analysis and profiling platform governed by the **Project Governance and State Machine (PGSM v1.0.0)** standard.

The project architecture separates observable communicative phenomena from analytical inferences, enforcing full provenance tracking from raw media/transcripts to synthesized reports.

## Governance & Physical Structure

- **Governance Model:** PGSM v1.0.0
- **Canonical Root:** `C:\Users\candy\Desktop\lil_projects\proff`
- **Current Structure Version:** `v1.0.0`
- **Authoritative State:** [`project_state/CURRENT_STATE.md`](project_state/CURRENT_STATE.md)
- **Agent Instructions:** [`AGENTS.md`](AGENTS.md)

## Directory Hierarchy

- `governance/` — Privacy, ethics, security boundaries, and naming standards.
- `project_state/` — Live state machine, phase roadmap, task register, architectural decisions, and immutable history snapshots.
- `inputs/` — Staged raw material and exports (isolated and git-ignored by default).
- `specifications/` — Canonical schema definitions and knowledge-base references.
- `pipeline/` — Multimodal processing modules (ingestion, transcription, analyzers, synthesis).
- `outputs/` — Derived analytical reports and generated communication passports.
- `tests/` — Automated test suites, privacy validations, and verification benchmarks.

## Privacy & Safety Core

Raw case communications, personal chat archives (such as `tg_save/`), biometric audio/video recordings, and individual identifiable data are strictly protected under [`governance/policies/privacy_boundary.md`](governance/policies/privacy_boundary.md). They are excluded from source control and isolated from third-party networks.

