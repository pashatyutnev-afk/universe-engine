# 00__INDEX_MANIFEST__KB

SCOPE: UE_V2
DOC_TYPE: INDEX_MANIFEST (KB)
LAYER: 05_KB
STATUS: ACTIVE
VERSION: 1.0.0
UID: UE.V2.KB.INDEX.MANIFEST.000
NAV_RULE: Use RAW links only
PURPOSE: Canonical KB entry map for NAV/ROUTER/PIPE. Proves KB availability without tree scans.

---
## [M] RULES (CANON)
- This manifest is the ONLY canonical entrypoint for KB layer navigation.
- Every KB module referenced by ROUTER/PIPE/GATES MUST be listed here with RAW.
- No PATH-only references in runtime. Use RAW only.
- Keep this file small and deterministic (no long prose). Output-first.

---
## [M] REQUIRED FOR START_SEQUENCE (S4 NAV)
NAV must be able to confirm KB access via:
- this manifest (SELF)
- KB pipeline contract
- KB root panel
- KB relation xref pack (gate/rubric/example linkage set)

If any required item missing → GAP.

---
## [M] INDEX (PATH → RAW)

### 0) SELF
- `UE_V2/05_KB/00__INDEX_MANIFEST__KB.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/00__INDEX_MANIFEST__KB.md

### 1) KB CORE (MUST)
- `UE_V2/05_KB/00__PIPELINE_CONTRACT__KB.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/00__PIPELINE_CONTRACT__KB.md
- `UE_V2/05_KB/01__KB_ROOT.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/01__KB_ROOT.md

### 2) KB RELATION XREF (GATES / RUBRICS / EXAMPLES) (MUST)
- `UE_V2/05_KB/40_RELATION_XREF/84__KB_EXAMPLE_TO_GATE_LINKING_RULE.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/84__KB_EXAMPLE_TO_GATE_LINKING_RULE.md
- `UE_V2/05_KB/40_RELATION_XREF/85__KB_EXAMPLE_LIBRARY_STRUCTURE_MAP.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/85__KB_EXAMPLE_LIBRARY_STRUCTURE_MAP.md
- `UE_V2/05_KB/40_RELATION_XREF/86__KB_EXAMPLE_USAGE_IN_DRILLS_RULE.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/86__KB_EXAMPLE_USAGE_IN_DRILLS_RULE.md
- `UE_V2/05_KB/40_RELATION_XREF/87__KB_DOMAIN_QA_CALIBRATION_PROTOCOL.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/87__KB_DOMAIN_QA_CALIBRATION_PROTOCOL.md
- `UE_V2/05_KB/40_RELATION_XREF/88__KB_GATE_DEFINITION_STANDARD.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/88__KB_GATE_DEFINITION_STANDARD.md
- `UE_V2/05_KB/40_RELATION_XREF/89__KB_GATE_CARD_TEMPLATE.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/89__KB_GATE_CARD_TEMPLATE.md
- `UE_V2/05_KB/40_RELATION_XREF/90__KB_GATE_TO_EXAMPLE_BINDING_RULE.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/90__KB_GATE_TO_EXAMPLE_BINDING_RULE.md
- `UE_V2/05_KB/40_RELATION_XREF/91__KB_GATE_EXEMPLAR_SET_TEMPLATE.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/91__KB_GATE_EXEMPLAR_SET_TEMPLATE.md
- `UE_V2/05_KB/40_RELATION_XREF/92__KB_GATE_LIBRARY_POLICY.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/92__KB_GATE_LIBRARY_POLICY.md
- `UE_V2/05_KB/40_RELATION_XREF/93__KB_GATE_DEPRECATION_AND_REPLACEMENT_RULE.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/93__KB_GATE_DEPRECATION_AND_REPLACEMENT_RULE.md
- `UE_V2/05_KB/40_RELATION_XREF/94__KB_GATE_VERSIONING_POLICY.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/94__KB_GATE_VERSIONING_POLICY.md
- `UE_V2/05_KB/40_RELATION_XREF/95__KB_GATE_CURATION_CHECKLIST.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/95__KB_GATE_CURATION_CHECKLIST.md
- `UE_V2/05_KB/40_RELATION_XREF/96__KB_QA_RUBRIC_STANDARD.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/96__KB_QA_RUBRIC_STANDARD.md
- `UE_V2/05_KB/40_RELATION_XREF/97__KB_QA_RUBRIC_CARD_TEMPLATE.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/97__KB_QA_RUBRIC_CARD_TEMPLATE.md
- `UE_V2/05_KB/40_RELATION_XREF/98__KB_QA_SCORING_CONSISTENCY_PROTOCOL.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/98__KB_QA_SCORING_CONSISTENCY_PROTOCOL.md
- `UE_V2/05_KB/40_RELATION_XREF/99__KB_QA_SCORE_REPORT_TEMPLATE.md` →
  https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/05_KB/40_RELATION_XREF/99__KB_QA_SCORE_REPORT_TEMPLATE.md

---
## [M] GATES
PASS if:
- SELF + KB CORE + KB RELATION XREF present
- all entries are RAW
GAP if:
- any MUST section missing
FAIL if:
- PATH-only refs used in runtime files

--- END.
