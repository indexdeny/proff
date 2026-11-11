# Customization Inventory — Antigravity Environment Audit

**Task ID:** `TZ-0002-environment-audit`  
**Phase:** PH-02  
**Date:** 2026-11-12T00:39:00+02:00  
**Project:** PsychoPassport Engine (`proff`)  
**Scope:** Read-Only Audit of Environment Customizations  
**Inspection Restriction:** `EXTERNAL_INSPECTION_REQUIRES_APPROVAL` (Direct external filesystem crawling forbidden; inventory derived from active session metadata and authorized IDE interfaces).

---

## 1. Summary of Discovered Customizations

| Category | Total Count | Workspace Scope | Builtin Scope | Global / Plugin Scope | Proff Relevance |
|---|---|---|---|---|---|
| **Rules** | 2 active (+2 proposed) | 1 (`AGENTS.md`) | 0 | 1 (`science/rules`) | Low (Global rule irrelevant to Proff) |
| **Skills** | 101 | 0 | 10 | 91 (21 global, 70 plugin) | Low (Most are GCP / Science / Android) |
| **Plugins** | 3 detected (+builtin) | 0 | Yes | 3 (`data-agent-kit`, `science`, `android-cli`) | Low |
| **MCP Servers** | 4 declared | 0 | 0 | 4 (`data-agent-kit`, `dak-data-agent-kit`, `dak-notebook`, `notebooks`) | Low |
| **Agents** | 4 builtin | 0 | 4 (`self`, `research`, `image-generator`, `browser`) | 0 | Medium (`self`, `research` useful) |
| **Hooks** | 1 detected | 0 | 0 | 1 (`SessionStart` via DAK) | Low |

---

## 2. Rules Inventory

| Rule Name | Origin | Scope | Source Location | Enabled | Loaded | Dependencies | Conflicts / Overlaps | Security Implication | Recommendation |
|---|---|---|---|---|---|---|---|---|---|
| **Workspace Invariants** | Workspace | Workspace (`proff`) | `AGENTS.md` | YES | YES | None | None | Enforces strict project boundary, privacy, and non-clinical status | `KEEP` |
| **Science Visualization Rules** | Plugin (`science`) | Global / Plugin | `~/.gemini/config/plugins/science/rules/AGENTS.md` | YES | YES | Mol* sidecar viewer | Overlaps with visualization priorities | Directs user to Mol* sidecar; irrelevant for Proff | `KEEP` (Global; do not alter without user consent) |
| **Additional Global Rules** | Global Config | Global | `~/.gemini/config/` | UNKNOWN | UNKNOWN | UNKNOWN | UNKNOWN | External inspection requires approval | `INVESTIGATE` (Requires user approval) |

---

## 3. Skills Inventory

### 3.1 Builtin Skills (Antigravity Core)
All 10 builtin skills are mounted by the IDE runtime:

| Skill Name | Scope | Enabled | Loaded | Purpose / Description | Recommendation |
|---|---|---|---|---|---|
| `agy-customizations` | Builtin | YES | On-Demand | Antigravity customization reference & architecture guide | `KEEP` |
| `antigravity-guide` | Builtin | YES | On-Demand | Comprehensive guide to Antigravity IDE and CLI | `KEEP` |
| `automation` | Builtin | YES | On-Demand | Interactive guide to create scheduled background automations | `KEEP` |
| `generative_ui` | Builtin | YES | On-Demand | Interactive HTML/UI rendering guide | `KEEP` |
| `migrate-agent-settings` | Builtin | YES | On-Demand | Migrates settings from Claude Code / Cursor / Codex | `KEEP` |
| `migrate-workflows` | Builtin | YES | On-Demand | Migrates legacy workflows to skills | `KEEP` |
| `plugin` | Builtin | YES | On-Demand | Manages and packages Antigravity plugins | `KEEP` |
| `swarm` | Builtin | YES | On-Demand | Multi-agent collaboration message board | `KEEP` |
| `swarm_monitor` | Builtin | YES | On-Demand | Swarm stall monitor | `KEEP` |
| `ui-plugin-navigation` | Builtin | YES | On-Demand | Sidecar / UI panel launcher pills | `KEEP` |

### 3.2 Global Config Skills (`~/.gemini/config/skills/`)
21 skills discovered in global user configuration. Note: 20 of these are **exact duplicates** of skills provided by `data-agent-kit-plugin`:

| Skill Name | Origin | Enabled | Loaded | Duplicate / Conflict | Recommendation |
|---|---|---|---|---|---|
| `accidental-data-loss-prevention` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `bigquery-data-transfer-service` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `building-data-apps` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `cloud-databases-onboarding` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `data-autocleaning` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `dataform-bigquery` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `dbt-bigquery` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `discovering-gcp-data-assets` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `enforcing-resource-attribution` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `gcp-data-pipelines` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `gcp-dataflow` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `gcp-pipeline-orchestration` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `gcp-pipeline-resource-provisioning` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `gcp-spark` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `gcp-spark-observability` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `gcp-spark-troubleshooting` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `managing-python-dependencies` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `ml-best-practices` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `notebook-guidance` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `schema-mapping` | Global | YES | On-Demand | Exact duplicate of `data-agent-kit-plugin` skill | `INVESTIGATE` / `REMOVE_AFTER_APPROVAL` |
| `skill-repair` | Global | YES | On-Demand | Unique to global config (repairs failed manifest) | `KEEP` |

### 3.3 Plugin Skills
- **`data-agent-kit-plugin` (22 skills):** 20 duplicated skills as listed above, plus `dak-setup` and `resolving-mcp-region-configs`. Recommendation: `DISABLE_PROPOSED` for `proff` workspace context.
- **`science` plugin (47 skills):** Covers genomics, structural biology, chemistry, and clinical databases (e.g. `alphafold-database-fetch-and-analyze`, `chembl-database`, `pymol`, `pubchem-database`, `blast`). Irrelevant to Proff communication pattern engine. Recommendation: `DISABLE_PROPOSED` for workspace context.
- **`android-cli-plugin` (3 skills):** `android-cli`, `android-device-hub`, `compose-preview`. Irrelevant to Proff backend/analysis workflows. Recommendation: `DISABLE_PROPOSED` for workspace context.

---

## 4. Plugins Inventory

| Plugin Identifier | Origin | Scope | Enabled | Loaded | Permissions / Features | Relevance to Proff | Recommendation |
|---|---|---|---|---|---|---|---|
| `data-agent-kit-plugin` | User Plugin | Global | YES | YES | MCP Tools, GCP CLI, SessionStart Hook | IRRELEVANT_COMPONENT (GCP data analysis) | `DISABLE_PROPOSED` |
| `science` | User Plugin | Global | YES | YES | Biology/Chemistry APIs, Mol* Sidecar, Rules | IRRELEVANT_COMPONENT (Structural biology) | `DISABLE_PROPOSED` |
| `android-cli-plugin` | User Plugin | Global | YES | YES | Android SDK, ADB, Sidecar Preview | IRRELEVANT_COMPONENT (Mobile UI development) | `DISABLE_PROPOSED` |

*Note: In accordance with Invariant I-04, no plugins have been disabled or deleted.*

---

## 5. MCP Servers Inventory

| Server Name | Origin | Enabled | Loaded Tools | Tool Types | Relevance to Proff | Recommendation |
|---|---|---|---|---|---|---|
| `data-agent-kit` | DAK Plugin | YES | 5 lazy tools | `get_active_editor_context`, `get_active_gcp_connection`, `render_chart`, etc. | IRRELEVANT | `KEEP` / Do not invoke |
| `data-agent-kit-plugin_dak-data-agent-kit` | DAK Plugin | YES | 0 active tools | Declared container | IRRELEVANT | `KEEP` / Do not invoke |
| `data-agent-kit-plugin_dak-notebook` | DAK Plugin | YES | 9 lazy tools | `create_notebook`, `read_cell`, `insert_cell`, etc. | IRRELEVANT (Duplicate of `notebooks`) | `KEEP` / Do not invoke |
| `notebooks` | Environment | YES | 11 lazy tools | `create_notebook`, `insert_code_cell`, `read_cell`, etc. | IRRELEVANT | `KEEP` / Do not invoke |

---

## 6. Agents & Subagents Inventory

| Agent Name | Type | Origin | Enabled | Role / Capability | Relevance to Proff | Recommendation |
|---|---|---|---|---|---|---|
| `self` | Subagent | Builtin | YES | Inherits parent agent's full configuration, tools, and model | HIGH (Can run delegated background tasks) | `KEEP` |
| `research` | Subagent | Builtin | YES | Read-only sandbox for exploring codebase and reading documentation | HIGH (Can explore safe files without mutation) | `KEEP` |
| `image-generator` | Subagent | Builtin | YES | Generates and edits images | LOW (Irrelevant for core profiling) | `KEEP` |
| `browser` | Subagent | Builtin | Excluded | Chrome DevTools web automation (excluded due to context budget) | LOW | `KEEP` |

---

## 7. Hooks Inventory

| Hook Event | Declaring Component | Script / Target | Enabled | Loaded | Purpose | Recommendation |
|---|---|---|---|---|---|---|
| `SessionStart` | `data-agent-kit-plugin` | `dak-setup` / environment check | UNKNOWN | UNKNOWN | Checks GCP ADC credentials and project setup on session startup | `INVESTIGATE` |
| Other Hooks | Global Config (`hooks.json`) | UNKNOWN | UNKNOWN | UNKNOWN | External inspection requires approval | `INVESTIGATE` |

