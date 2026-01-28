# 19__IO_TYPES

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: STD
UID: UE.V2.STD.IO_TYPES.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Единый словарь типов входов/выходов (IO_IN/IO_OUT) для совместимости сущностей.

---

## [M] INTENT
Сущности стыкуются не "по памяти", а по IO типов. Это убирает хаос и делает сборку цепочки автоматической через REG+XREF.

---

## [M] IO_TYPES (CORE)
- IO.BRIEF
- IO.PLAN
- IO.ROUTE
- IO.KB_SCOPE
- IO.OPTIONS
- IO.DECISION
- IO.REPORT.CTL
- IO.REPORT.VAL
- IO.REPORT.QA
- IO.DELTA
- IO.PACK
- IO.BASELINE

---

## [M] IO_TYPES (MUSIC)
- IO.MUSIC.HOOK_OPTIONS
- IO.MUSIC.STRUCTURE_MAP
- IO.MUSIC.PALETTE_SPEC
- IO.MUSIC.PROMPT_SPEC
- IO.MUSIC.GEN_PLAN
- IO.MUSIC.SELECTION
- IO.MUSIC.MIX_PLAN
- IO.MUSIC.MASTER_PLAN
- IO.MUSIC.TRACK_QA_REPORT
- IO.MUSIC.RELEASE_PACK

---

## [M] IO_TYPES (VIS)
- IO.VIS.PROMPT_SPEC
- IO.VIS.SHOT_RULES
- IO.VIS.PACK

---

## [M] IO_TYPES (LOR)
- IO.LOR.NODE
- IO.LOR.CANON_UPDATE
- IO.LOR.XREF_PACK

---

## [M] IO_COMPATIBILITY_RULES
1) Следующий шаг может принимать только IO, который совпадает с его IO_IN.
2) Если IO тип отсутствует в словаре, это GAP (добавить IO_TYPE).
3) ORC обязан указывать IO_OUT каждого шага и IO_IN следующего.

---

## [M] GATES
PASS если:
- для каждого шага указан IO_OUT, и он существует в словаре
REWORK если:
- IO_OUT указан, но не совпадает с IO_IN следующего шага
STOP если:
- пайп не может определить IO_OUT
