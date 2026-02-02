FILE: UE_V2/03_ENT/90_XREF/09__MAP__ENG_to_ORC__XREF.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: XREF_MAP
DOMAIN: XREF
UID: UE.V2.XREF.ENG_TO_ORC.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# XREF — ENG to ORC

PURPOSE:
Правила handoff от ENG к ORC: что считается "готовым выходом" и что возвращать на доработку.

---

## HANDOFF RULES

| ENG_OUTPUT | ORC_EXPECTS | IF_MISSING |
|---|---|---|
| DRAFT_ARTIFACT | структура соответствует шаблону | return to ENG.BUILD_DRAFT |
| STYLE_TOKEN | стиль подтверждён SPC | request SPC fix |
| KB_TOKEN | ограничения применены | route to CTL/VAL |
| OUTPUT_PACK | упаковано единым документом | run ENG.PACK_OUTPUT |
