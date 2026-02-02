FILE: UE_V2/03_ENT/90_XREF/02__XREF__ROLE_MAP__XREF.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: XREF_MAP
DOMAIN: XREF
UID: UE.V2.XREF.ROLE_MAP.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# XREF — ROLE MAP

PURPOSE:
Определяет роли (типы сущностей) и их обязательность по доменам и режимам.

---

## ROLE DEFINITIONS (brief)

| ROLE | TYPE | WHAT IT DOES |
|---|---|---|
| SPC | Specialist | постановка, критерии, смысл, ограничения |
| ORC | Orchestrator | пошаговый прогон, стыковка сущностей |
| ENG | Engine | генерация/преобразование/сборка контента |
| CTL | Controller | ограничения, запреты, compliance |
| VAL | Validator | проверки по правилам, гейты PASS/STOP/GAP |
| QA | Quality | тест сценарии, дефекты, регресс |
| XREF | Crossref | карты связей и цепочки |
| KB | Knowledge | знания и границы |

---

## REQUIRED ROLES MATRIX

Legend:
- M = MUST
- O = OPTIONAL

| DOMAIN | FAST | RELEASE_READY | MASTERPIECE |
|---|---|---|---|
| DOM_AUD | SPC(M) ORC(M) ENG(M) CTL(O) VAL(M) QA(O) | SPC(M) ORC(M) ENG(M) CTL(M) VAL(M) QA(M) | SPC(M) ORC(M) ENG(M) CTL(M) VAL(M) QA(M) XREF(M) |
| DOM_VIS | SPC(M) ORC(M) ENG(M) CTL(O) VAL(M) QA(O) | SPC(M) ORC(M) ENG(M) CTL(M) VAL(M) QA(M) | SPC(M) ORC(M) ENG(M) CTL(M) VAL(M) QA(M) XREF(M) |
| DOM_LOR | SPC(M) ORC(M) ENG(M) CTL(O) VAL(M) QA(O) | SPC(M) ORC(M) ENG(M) CTL(M) VAL(M) QA(M) | SPC(M) ORC(M) ENG(M) CTL(M) VAL(M) QA(M) XREF(M) |

NOTES:
- Если роль обязательна и не найдена в домене → GAP (потому что можно временно работать default-ролями).
- STOP только если отсутствует минимальный системный слой (BOOT/NAV/PIPE/LOG/REG).
