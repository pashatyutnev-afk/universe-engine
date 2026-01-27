# FILE: UE_V2/05_KB/07__KB_LOR.md
SCOPE: UE_V2
LAYER: 05_KB
DOC_TYPE: KB_DOMAIN
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.KB.LOR.001
OWNER: SYSTEM
TITLE: KB LORE (METRICS→CANON)

## MARKERS
- [M] DEFINITIONS
- [M] MAPPINGS
- [M] CONSTRAINTS

## [M] DEFINITIONS
- ID: LOR.RI_LANG | TYPE: DEF | BODY: падение RI = распад языка/коммуникации в каноне (событийный триггер).
- ID: LOR.ARC | TYPE: DEF | BODY: “Resonance Arc” = кривая воздействия (alienation/rage/hope) по релизным фазам.

## [M] MAPPINGS
- ID: MAP.RI.DECAY | TYPE: MAP | BODY: если RI_t < 0.62 → канон: “сбой смысла”, сцены распада речи/сигналов.
- ID: MAP.LRA.COLLAPSE | TYPE: MAP | BODY: если LRA > 12 LU и LAW-13 активен → канон: “коллапс пространства”, переход в Zero Point.
- ID: MAP.CF.RAGE | TYPE: MAP | BODY: рост CF при стабильном RI → “ярость/драйв” доминирует, конфликт ускоряется.

## [M] CONSTRAINTS
- ID: CST.CANON_LOCK | TYPE: CST | BODY: триггеры обязаны быть детерминированы метриками; без метрики → нет триггера (иначе шум).
