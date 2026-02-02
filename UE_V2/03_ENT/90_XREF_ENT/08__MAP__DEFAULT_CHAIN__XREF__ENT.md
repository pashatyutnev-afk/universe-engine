FILE: UE_V2/03_ENT/90_XREF/08__MAP__DEFAULT_CHAIN__XREF.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: XREF_CHAIN
DOMAIN: XREF
UID: UE.V2.XREF.DEFAULT_CHAIN.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# XREF — DEFAULT CHAIN

PURPOSE:
Дефолтная цепочка исполнения для любого домена, чтобы:
- не начинать с нуля,
- иметь стартовые точки для продолжения,
- резать работу на шаги.

---

## DEFAULT CHAIN (global)

1) SPC.BRIEF_BUILDER
2) ORC.ROUTE_EXEC
3) CTL.GUARDRAILS
4) ENG.BUILD_DRAFT
5) VAL.VALIDATE
6) QA.QUALITY_PASS
7) ENG.PACK_OUTPUT
8) ORC.LOG_AND_ARCHIVE

---

## START POINTS (universal)

| START_POINT_ID | WHEN USED | ENTRY STEP |
|---|---|---|
| SP.START | новый прогон | step 1 |
| SP.ROUTE_FIX | ошибка маршрута/домена | step 2 |
| SP.GUARD_FIX | нарушение ограничений | step 3 |
| SP.REWRITE_SECTION | косяк части текста/куплета | step 4 (draft rebuild for section) |
| SP.VAL_FAIL | валидатор завалил | step 5 |
| SP.QA_FAIL | качество не прошло | step 6 |
| SP.PACK_ONLY | всё ок, надо упаковать | step 7 |
| SP.LOG_ONLY | только запись в логи | step 8 |

RULE:
- стартовая точка выбирается ORC по FAIL_CODE или по запросу пользователя.
- цепочка не пересоздаётся заново, если можно продолжить с нужного SP.
