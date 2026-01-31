FILE: UE_V2/03_ENT/90_XREF/10__MAP__ORC_to_SPC__XREF.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: XREF_MAP
DOMAIN: XREF
UID: UE.V2.XREF.ORC_TO_SPC.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# XREF — ORC to SPC

PURPOSE:
Чекпоинты, когда ORC обязан возвращаться к SPC, чтобы смысл не развалился.

---

## CHECKPOINTS

| ORC_EVENT | SPC_ACTION |
|---|---|
| ambiguous task | уточнить критерии и формат |
| domain unclear | выбрать домен и тип артефакта |
| constraint conflict | приоритизировать ограничения |
| user wants partial rewrite | выбрать START_POINT и критерии правки |
| quality not hit | усилить критерии (хук/тон/структура) |

RULE:
- SPC не обязан хранить ссылки.
- SPC возвращает только токены: BRIEF_TOKEN, SUCCESS_CRITERIA, CONSTRAINTS, START_POINT.
