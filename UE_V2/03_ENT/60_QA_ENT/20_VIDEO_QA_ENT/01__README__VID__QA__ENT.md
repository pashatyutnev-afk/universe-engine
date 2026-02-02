FILE: UE_V2/03_ENT/60_QA_ENT/20_VIDEO_QA_ENT/01__README__VID__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 20_VIDEO_QA_ENT
DOC_TYPE: README
DOMAIN: VID_QA_ENT
UID: UE.V2.ENT.QA.VID.README.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: Use KEYS, resolve RAW via INDEX_MANIFEST

---

## [M] PURPOSE
VID QA — минимальные проверки видео артефактов на регресс и стабильность качества между итерациями.
На старте реалм содержит regression guard как обязательный гейт.

## [M] HOW TO USE (keys only)
1) Открой `00__INDEX_MANIFEST__VID__QA__ENT.md`.
2) Возьми KEY нужной проверки: `QA.VID.REGRESSION_GUARD`.
3) Применяй к итерациям: baseline vs current notes -> decision -> required fixes.

## [M] EXPECTED OUTPUTS
- QA_DECISION: PASS|WARN|ASK|FAIL
- QA_FINDINGS: кратко
- REQUIRED_FIXES: минимально
- ISSUES: опционально

## [M] NON-GOALS
- Не делает монтажных решений.
- Не выбирает стиль вместо brief.
- Не использует внешние источники.
