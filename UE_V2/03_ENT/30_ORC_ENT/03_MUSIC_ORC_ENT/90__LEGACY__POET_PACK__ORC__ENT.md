FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/90__LEGACY__POET_PACK__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: LEGACY_ORC_ENT
UID: UE.V2.ENT.ORC.LEGACY.POET_PACK.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: LEGACY_POET_PACK_ORC_ENT
- ENTITY_CLASS: ORC (LEGACY)
- UID: UE.V2.ENT.ORC.LEGACY.POET_PACK.001

## [M] PURPOSE
Back-compat пакет для старого “поэт-флоу”: быстрый бриф -> черновик -> правка -> упаковка.
Использовать только когда явно нужен упрощённый путь или совместимость со старым форматом.

## [M] INPUTS / OUTPUTS
- Inputs: [TASK_TEXT, MODE_HINT?]
- Outputs: [LEGACY_POET_TOKEN, PROMPT_PACK?, FAIL_CODE?]

## [M] GATES
- PASS: legacy режим явно выбран, правила соблюдены
- FAIL: конфликтует с текущими запретами/политиками

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: token -> PROMPT_PACKAGER / QA_CHECKS

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
