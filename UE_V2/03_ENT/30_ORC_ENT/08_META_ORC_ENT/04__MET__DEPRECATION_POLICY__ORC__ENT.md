FILE: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/04__MET__DEPRECATION_POLICY__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 08_META_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MET_ORC_ENT
UID: UE.V2.ENT.ORC.MET.DEPRECATION_POLICY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MET_DEPRECATION_POLICY
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MET.DEPRECATION_POLICY.001

## [M] PURPOSE
Определяет правила деприкации: когда можно пометить DEPRECATED, что должно остаться для совместимости, какие миграционные заметки обязательны.
Возвращает DEPRECATION_TOKEN и REQUIRED_GATES.

## [M] INPUTS / OUTPUTS
- Inputs: [TASK_TEXT, TARGET_KEYS?, UID_NORMALIZATION_TOKEN?]
- Outputs: [DEPRECATION_TOKEN, FAIL_CODE?]

## [M] DEPRECATION_TOKEN (minimum)
- TARGET
- REASON
- DEPRECATION_LEVEL (soft/hard)
- BACKCOMPAT_NOTES
- MIGRATION_STEPS
- REQUIRED_LOGS
- REQUIRED_GATES

## [M] KB SCOPE
- KB Inputs: [deprecation policy rules]
- KB Outputs: [deprecation token]
- KB Boundaries: [не выполнять реальные изменения, только правила/план]
- KB RAW refs: []

## [M] GATES
- PASS: план деприкации безопасен и проверяем
- FAIL: нет target или миграция не определена

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: DEPRECATION_TOKEN -> caller realm / governance (if needed)

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
