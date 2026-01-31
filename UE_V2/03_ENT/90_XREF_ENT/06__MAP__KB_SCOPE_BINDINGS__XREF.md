FILE: UE_V2/03_ENT/90_XREF/06__MAP__KB_SCOPE_BINDINGS__XREF.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: XREF_MAP
DOMAIN: XREF
UID: UE.V2.XREF.KB_SCOPE_BINDINGS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# XREF — KB SCOPE BINDINGS

PURPOSE:
Связывает домены с типовыми KB_SCOPE, чтобы система знала что грузить и что считать границами.

---

## BINDINGS

| DOMAIN | KB_SCOPE_INPUTS | KB_SCOPE_OUTPUTS | KB_SCOPE_BOUNDARIES |
|---|---|---|---|
| DOM_AUD | жанр, вокал, темп, запреты, структура | prompt_spec, lyrics, output_pack | no artist names, no exclamation marks, originality |
| DOM_VIS | стиль, формат, размеры, запреты | image_spec, layout, output_pack | brand rules, format constraints |
| DOM_LOR | канон, эпоха, персонажи, ограничения | scene/lore pack | canon compliance, no contradictions |

NOTE:
- конкретные KB файлы адресуются через KB индексы, но логика привязки фиксируется здесь.
