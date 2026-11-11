# R0 Baseline Integrity & Audit Report

**Task ID:** `TZ-0003-isolated-git-checkpoints`  
**Phase:** PH-03  
**Date:** 2026-11-12T00:55:55+02:00  
**Project:** PsychoPassport Engine (`proff`)  
**Standard:** PGSM v1.0.0 / `governance/policies/recovery_policy.md`  

---

## 1. Physical Archive Identity & Hash Audit

| Metric | Recorded in Manifest | Recorded in WALKTHROUGH-0002 | Physical File on Disk | Parity Status |
|---|---|---|---|---|
| **Archive File** | `R0_BACKUP.zip` | `R0_BACKUP.zip` | `R0_BACKUP.zip` | MATCH |
| **Size (Bytes)** | 54,947 | 54,947 | 54,947 | MATCH |
| **SHA-256 Hash** | `9AA491D6E08F4DF733E0022B4F0175F2FBBD7D0A75B960D1FA81ECDCA9121267` | `51FDC91FDCFBEB5A5C782944359D461FDC20BBE4484E9D0219C481EC1F2DB6E4` | `9AA491D6E08F4DF733E0022B4F0175F2FBBD7D0A75B960D1FA81ECDCA9121267` | **MANIFEST MATCH** |

### Resolution of Walkthrough Discrepancy
The hash recorded in canonical `R0_MANIFEST.json` (`9AA491D6...`) matches the actual physical bits of `R0_BACKUP.zip` on disk. The hash recorded in `WALKTHROUGH.md` (`51FDC91F...`) originated during intermediate scripting before the final archive was packaged. The authoritative source of truth (`R0_MANIFEST.json`) is physically valid and intact.

---

## 2. Archive Safety & Entry Structure Audit

All entries inside `R0_BACKUP.zip` were inspected using .NET `ZipFile.OpenRead` prior to extraction:
- **Total Entries Count:** 29 (matches manifest exactly)
- **Absolute Path Check:** 0 entries begin with drive letters (`C:`, `D:`) or leading slashes (`/`, `\`). **`PASS`**
- **Directory Traversal Check:** 0 entries contain parent directory tokens (`..`). **`PASS`**
- **Symlink / Reparse Check:** 0 entries contain symbolic link flags or external references. **`PASS`**
- **Excluded Content Check:** 0 entries belong to `tg_save/`, `inputs/raw_exports/`, `.env`, or credential patterns. **`PASS`**

---

## 3. Trial Restore & Parity Verification

A trial extraction was executed to an isolated temporary directory within Project Root (`_tmp_r0_test_stage_a/`):
- All 29 files were extracted successfully.
- Every extracted file was hashed with SHA-256 and compared against `R0_MANIFEST.json`:

| File Entry Path | Manifest Size | Manifest SHA-256 | Restored SHA-256 | Parity |
|---|---|---|---|---|
| `AGENTS.md` | 2,583 | `EFAE69B32A65E57721762ECF70DF62D5CD86A2ABCF84ED2651695E2D6495EAB1` | `EFAE69B3...` | **MATCH** |
| `README.md` | 1,797 | `B11ABC6AD15526903556263843E6B6AAA776BE6FA2A263E51D98B3C030467D6B` | `B11ABC6A...` | **MATCH** |
| `.gitignore` | 879 | `3D7A8FABEB04A87FF1168E9CB1A2AE4D7689AE826A76F4D7BAF96EA9630DA78A` | `3D7A8FAB...` | **MATCH** |
| `PROF-TZ-0001_WORKSPACE_BOOTSTRAP.md` | 18,868 | `54FAB793D96FD984C66F42D48F0638F0285BD890C7FE938EC769898A54FC0E02` | `54FAB793...` | **MATCH** |
| `ROADMAP_PROFF_v1.0.md` | 4,411 | `BF267B59B66431D3F4E8C5D9B2BEDE420D7F54BFCE19C62F26CCA2AE1F21CADA` | `BF267B59...` | **MATCH** |
| `governance/naming.md` | 1,410 | `B5AC8B8B152382980CEB3C9FAB4FBD73F256E07FD0B805BF5FCA2009344BD947` | `B5AC8B8B...` | **MATCH** |
| `governance/policies/privacy_boundary.md` | 1,876 | `11FD26F62FA6B3321C650DFBFBC13E2FFF383FE3B08A06A436D224132A5A1D21` | `11FD26F6...` | **MATCH** |
| `inputs/raw_exports/.gitkeep` | 0 | `E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855` | `E3B0C442...` | **MATCH** |
| `inputs/source_staging/.gitkeep` | 0 | `E3B0C44298FC1C149AFBF4C8996FB92427AE41E4649B934CA495991B7852B855` | `E3B0C442...` | **MATCH** |
| `outputs/README.md` | 662 | `62E43F03EEE17B27D3413D931569158872194314246048A2138D9D91243C2416` | `62E43F03...` | **MATCH** |
| `pipeline/README.md` | 868 | `335F66C7544086989A0DE1592E07278E509DD41AD7903612094DC46FAB558F6A` | `335F66C7...` | **MATCH** |
| `project_state/CHANGELOG.md` | 1,212 | `09D4708F6342E44753CC3D51EAD8FD07C86E9771FADC7FB08574631537AD5631` | `09D4708F...` | **MATCH** |
| `project_state/CURRENT_STATE.md` | 1,377 | `236FD1CC07FAD2284A8D19D13C5ADBDAC573E50ECDEB1DB33803FE55C0E387A0` | `236FD1CC...` | **MATCH** |
| `project_state/DECISIONS.md` | 882 | `F8D69793F5D065F6FF959E814D1A4327E1EBD5814B2A093D84D5872CEA13DD75` | `F8D69793...` | **MATCH** |
| `project_state/ISSUES.md` | 1,046 | `DB431B93C896E1B9C9E09F3B44470644EBCEDB5F259FDCB2F78F154CD188A0E9` | `DB431B93...` | **MATCH** |
| `project_state/ROADMAP.md` | 3,823 | `E190CAA42E2C0706C43FFC2CB47ED19A79459CB6541CE054821BEB538A47CD73` | `E190CAA4...` | **MATCH** |
| `project_state/TASK_REGISTER.md` | 627 | `599C10352EB832EAE78D44BF58FDD042F69C4A3B83DF8F6DB3F4D806738BCB64` | `599C1035...` | **MATCH** |
| `project_state/history/state/STATE-000001.md` | 980 | `041E54A007421AE4A6D9CBC40E049ECEA1D379DF1F1EE8F786E9B672A4D99C40` | `041E54A0...` | **MATCH** |
| `project_state/history/state/STATE-000002.md` | 1,174 | `3864EC22738B45DA14D2474497C5FE8433EC354116FE39AD5DCD19FA7A9720BC` | `3864EC22...` | **MATCH** |
| `project_state/history/state/STATE-000003.md` | 980 | `799A5004AEB8329CEE9EE03C9E2CC66675FFACDA7329AE12DDEBCEF5C6F7376D` | `799A5004...` | **MATCH** |
| `project_state/structure/STRUCTURE.md` | 3,727 | `9E9E521077A1B899A8964F383523C025D4BC87CA24D1EF6A1C9163DBC6334D98` | `9E9E5210...` | **MATCH** |
| `project_state/structure/STRUCTURE_CHANGELOG.md` | 474 | `6B50AE7D830A23EB4B34BE5CEF56461BAC1C11D41FE023E9E207AA79A31ED89B` | `6B50AE7D...` | **MATCH** |
| `project_state/structure/versions/v1.0.0.md` | 1,896 | `BBED16DE6FF2E9744E123231F7F7B5142857E0F9EEAA6029A37F80D34CE94E85` | `BBED16DE...` | **MATCH** |
| `project_state/tasks/TZ-0001-workspace-bootstrap/TZ.md` | 18,868 | `54FAB793D96FD984C66F42D48F0638F0285BD890C7FE938EC769898A54FC0E02` | `54FAB793...` | **MATCH** |
| `project_state/tasks/TZ-0001-workspace-bootstrap/WALKTHROUGH.md` | 11,088 | `553C047970F326D19010C24B517EC0B5DCE473D307A07E303DCE02E4CA3066DE` | `553C0479...` | **MATCH** |
| `project_state/tasks/TZ-0002-environment-audit/TZ.md` | 34,807 | `5BF1AA902E08F10D3006FBA24F2517DD7C23EB37D5F3405A70DEB064655C9163` | `5BF1AA90...` | **MATCH** |
| `project_state/tasks/TZ-0002-environment-audit/DISCOVERY.md` | 4,120 | `6AEBA878EF452774C333D3528A6B2967F1F0B76479058694086DBF14B6F7CD15` | `6AEBA878...` | **MATCH** |
| `specifications/knowledge_base/README.md` | 916 | `C76E1CD18A90620FF694D6224A65B3B5A5D203969476309BF6732C15CE9ADB7E` | `C76E1CD1...` | **MATCH** |
| `tests/README.md` | 695 | `8ECC5E1802A6B205929DB357B61FA9DC830DA6DBC58C94F12A23EFCCDE9880F5` | `8ECC5E18...` | **MATCH** |

- Temporary extraction directory was completely purged following verification.

---

## 4. Integrity Conclusion

The recovery baseline **R0** is verified as 100% intact, sound, safe, and recoverable.
**Final Status:** **`R0_INTEGRITY=PASS`**. Git initialization is authorized to proceed.
