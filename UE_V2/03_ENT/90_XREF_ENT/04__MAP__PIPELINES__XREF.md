FILE: UE_V2/03_ENT/90_XREF/04__MAP__PIPELINES__XREF.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: XREF_MAP
DOMAIN: XREF
UID: UE.V2.XREF.PIPELINES_MAP.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# XREF — PIPELINES MAP

PURPOSE:
Связка домен → какой пайп использовать и когда.

---

## PIPELINE SELECTION TABLE

| DOMAIN | DEFAULT_PIPE_KEY | DOMAIN_PIPE_KEY | TRIGGERS |
|---|---|---|---|
| DOM_AUD | PIPE.DEFAULT | PIPE.DOM_AUD.DEFAULT | prompt+lyrics, audio pack, mix notes |
| DOM_VIS | PIPE.DEFAULT | PIPE.DOM_VIS.DEFAULT | cover, banner, style sheet |
| DOM_LOR | PIPE.DEFAULT | PIPE.DOM_LOR.DEFAULT | lore pack, scene pack, canon spec |

NOTES:
- Если доменный пайп отсутствует → fallback на PIPE.DEFAULT (это GAP, не STOP).
