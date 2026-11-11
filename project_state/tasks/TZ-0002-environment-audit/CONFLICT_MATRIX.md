# Conflict Classification & Decision Matrix

**Task ID:** `TZ-0002-environment-audit`  
**Phase:** PH-02  
**Date:** 2026-11-12T00:39:30+02:00  
**Project:** PsychoPassport Engine (`proff`)  
**Standard:** PGSM v1.0.0  

---

## 1. Conflict Classification Taxonomy

The following standardized conflict classifications were evaluated against all discovered customizations:
- `EXACT_DUPLICATE`: Component exists in multiple locations with identical identifier and implementation.
- `SEMANTIC_OVERLAP`: Separate components providing identical or heavily overlapping capabilities.
- `CONTRADICTORY_RULE`: Direct logical collision between behavioral guidelines.
- `STALE_CONFIGURATION`: Component referring to unconfigured or missing external infrastructure.
- `OVERPRIVILEGED_COMPONENT`: Component holding tools or permissions beyond required scope.
- `IRRELEVANT_COMPONENT`: Fully functional component belonging to an unrelated domain (GCP, Android, Biology).
- `UNKNOWN`: Insufficient metadata to establish conflict or compatibility.

---

## 2. Identified Conflicts Matrix

| ID | Conflict Class | Involved Components | Provenance / Paths | Severity | Description & Architectural Impact |
|---|---|---|---|---|---|
| **C-01** | `EXACT_DUPLICATE` | 20 GCP/Data Skills | `~/.gemini/config/skills/<name>` vs. `~/.gemini/config/plugins/data-agent-kit-plugin/skills/<name>` | MEDIUM | 20 skills are registered twice in Antigravity's active skill catalog, inflating prompt overhead and creating resolution ambiguity. |
| **C-02** | `SEMANTIC_OVERLAP` | MCP Notebook Tools | `data-agent-kit-plugin_dak-notebook` vs. `notebooks` | LOW | Both MCP servers expose identical Jupyter notebook tools (`create_notebook`, `read_cell`, `insert_cell`, `replace_cell`, `delete_cell`). |
| **C-03** | `IRRELEVANT_COMPONENT` | Science Plugin (47 skills) | `~/.gemini/config/plugins/science/` | LOW | Heavy structural biology, cheminformatics, and genetics skills loaded into memory during social/linguistic analysis. |
| **C-04** | `IRRELEVANT_COMPONENT` | Android Plugin (3 skills) | `~/.gemini/config/plugins/android-cli-plugin/` | LOW | Android SDK, device mirroring, and Jetpack Compose tools present in Python/PowerShell backend workspace. |
| **C-05** | `STALE_CONFIGURATION` | `dak-setup` / GCP integrations | `data-agent-kit-plugin` | LOW | Prompts user on unconfigured GCP environment; Proff strictly disallows unauthorized cloud data transfers. |
| **C-06** | `SEMANTIC_OVERLAP` | Visualization Rule | `~/.gemini/config/plugins/science/rules/AGENTS.md` | LOW | Mandates Mol* sidecar priority; does not directly contradict Proff text analysis, but could cause priority conflicts if general charts are generated. |

---

## 3. Decision & Recommendation Matrix

| Component | Current Scope | Classification | Action Recommendation | Rationale / Execution Condition |
|---|---|---|---|---|
| `AGENTS.md` (Workspace root) | Workspace | Normal Baseline | **`KEEP`** | Authoritative workspace rules, startup order, and invariants. |
| Builtin Skills (10 skills) | Builtin | Core System | **`KEEP`** | Required for Antigravity core IDE operations and progressive workflows. |
| Duplicate Standalone Skills (20 skills in `~/.gemini/config/skills/`) | Global | `EXACT_DUPLICATE` | **`REMOVE_AFTER_APPROVAL`** | User should remove the 20 redundant standalone skill folders from `~/.gemini/config/skills/` after explicit approval, retaining plugin-managed versions. |
| `skill-repair` | Global | Normal Baseline | **`KEEP`** | Unique utility skill for repairing manifest issues; no duplicate. |
| `data-agent-kit-plugin` | Plugin | `IRRELEVANT_COMPONENT` | **`DISABLE_PROPOSED`** | Proff does not use BigQuery or GCP pipelines. Recommend disabling for this workspace once workspace-scoped plugin disabling is supported. |
| `science` plugin | Plugin | `IRRELEVANT_COMPONENT` | **`DISABLE_PROPOSED`** | Irrelevant domain (cheminformatics/biology). Recommend disabling for this workspace once supported. |
| `android-cli-plugin` | Plugin | `IRRELEVANT_COMPONENT` | **`DISABLE_PROPOSED`** | Irrelevant domain (Android mobile apps). Recommend disabling for this workspace once supported. |
| `notebooks` MCP Server | Environment | `SEMANTIC_OVERLAP` | **`KEEP`** | Retain default system notebook provider; ignore DAK duplicate. |
| `data-agent-kit-plugin_dak-notebook` | Plugin MCP | `SEMANTIC_OVERLAP` | **`DISABLE_PROPOSED`** | Redundant with standard `notebooks` MCP server. |
| `data-agent-kit` MCP Server | Plugin MCP | `IRRELEVANT_COMPONENT` | **`DISABLE_PROPOSED`** | Unused in local PsychoPassport processing. |
| Subagents (`self`, `research`) | Builtin | Core System | **`KEEP`** | Directly applicable for pair programming, analysis, and research tasks. |
| Subagents (`image-generator`, `browser`) | Builtin | Core System | **`KEEP`** | Passive builtin capabilities; no negative interference. |

*Crucial Governance Note: In accordance with Invariants I-02 and I-04, all actions above marked `DISABLE_PROPOSED` or `REMOVE_AFTER_APPROVAL` are documented recommendations only. Neither this agent nor this task executes modifications against global or external plugin configurations without explicit owner instructions.*

