# Privacy & Security Boundary Policy

**Project:** PsychoPassport Engine (`proff`)  
**Status:** ENFORCED  
**Effective Date:** 2026-11-12  

---

## 1. Core Principles

1. **Local Boundary Isolation**: All processing, analysis, and intermediate representations must remain strictly within the verified workspace root (`C:\Users\candy\Desktop\lil_projects\proff`). No automated external transmission or unauthorized cloud sync of case data is permitted.
2. **Raw Data Segregation**: Personal chat archives (e.g. `tg_save/`), raw multimedia recordings, and extracted transcripts must reside exclusively in git-ignored locations (`inputs/raw_exports/`, `inputs/source_staging/`, `tg_save/`). They must never be staged or committed to version control.
3. **Non-Clinical Boundary**: The platform is restricted to descriptive analysis of communicative patterns, interaction dynamics, and linguistic consistency. It is strictly prohibited from inferring psychiatric diagnoses, mental disorders, or clinical pathology.
4. **Observation vs. Inference Separation**: All analytical assertions must explicitly distinguish between direct, verifiable observations (timestamps, acoustic metrics, exact transcripts) and derived interpretive hypotheses.
5. **Human Oversight & Review**: No automated profiling artifact may be treated as finalized without human review, evaluation of alternative hypotheses, and verification of consent boundaries.

---

## 2. Technical Safeguards

- `.gitignore` enforces exclusion of secrets, `.env`, audio/video formats (`.ogg`, `.mp3`, `.wav`, `.mp4`), and export archives.
- Automated tests in `tests/` must verify ignore patterns and ensure zero data leakage before any repository checkpoint.
- Any logging, task walkthrough, or error report must record only cryptographic hashes and relative paths, redacting all personal identifying information (PII).

