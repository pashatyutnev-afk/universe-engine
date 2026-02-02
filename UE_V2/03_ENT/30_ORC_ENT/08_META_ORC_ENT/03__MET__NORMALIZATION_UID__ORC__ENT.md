FILE: UE_V2/03_ENT/30_ORC_ENT/08_META_ORC_ENT/03__MET__NORMALIZATION_UID__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 08_META_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MET_ORC_ENT
UID: UE.V2.ENT.ORC.MET.NORMALIZATION_UID.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MET_NORMALIZATION_UID
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MET.NORMALIZATION_UID.001

## [M] PURPOSE
Нормализует UID/CHANGE_ID как рекомендацию (token-only) по UID_RULES hook.
Не выполняет запись в репо. Выдаёт UID_NORMALIZATION_TOKEN: что должно быть приведено к канону.

## [M] INPUTS / OUTPUTS
- Inputs: [DRAFT_OUTPUT?, TEMPLATE_APPLY_NOTES, UID_RULES_HINT?]
- Outputs: [UID_NORMALIZATION_TOKEN, FAIL_CODE?]

## [M] UID_NORMALIZATION_TOKEN (minimum)
- DETECTED_UIDS
- SUGGESTED_UIDS
- CHANGE_ID_SUGGESTIONS
- UID_RULES_VERSION_HINT
- NOTES

## [M] KB SCOPE
- KB Inputs: [uid rules (when provided), draft headers]
- KB Outputs: [normalization token]
- KB Boundaries: [не выдумывать UID_RULES; ждать источник]
- KB RAW refs: []

## [M] GATES
- PASS: предложения не конфликтуют и достаточны
- FAIL: UID_RULES требуется, но не предоставлен и нельзя безопасно вывести

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA, CTL]
- Handoff: UID_NORMALIZATION_TOKEN -> DEPRECATION_POLICY / caller

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
