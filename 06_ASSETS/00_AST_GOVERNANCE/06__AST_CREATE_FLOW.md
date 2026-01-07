# AST CREATE FLOW — BOOTSTRAP
FILE: 07_ASSETS/00_AST_GOVERNANCE/06__AST_CREATE_FLOW.md

SCOPE: Universe Engine / Assets Workflow
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Процедура создания ассетов без ошибок.

SOURCE OF TRUTH:
- AST Registry: `07_ASSETS/00_AST_GOVERNANCE/02__INDEX__AST_GLOBAL_REGISTRY.md`
- AST Storage: `07_ASSETS/00_AST_GOVERNANCE/04__AST_STORAGE_MAP.md`
- AST Template: `07_ASSETS/00_AST_GOVERNANCE/05__TEMPLATE__AST_PASSPORT.md`

---

## 0) CORE LAW
Ассет существует только после:
(1) паспорт + (2) запись в AST Registry.

---

## 1) CREATE STEPS
1) Выбери CATEGORY (IMG/AUD/VID/PRM/REF)
2) Выбери FAMILY (VIS/SND/GEN/…)
3) Сгенерируй UID: `UE.AST.<CATEGORY>.<FAMILY>.<NAME>`
4) Создай паспорт:
   `07_ASSETS/<bucket>/<UID>.md`
5) Укажи REF_UID (если ассет обслуживает сцену/стек)
6) Запиши в AST Registry

---

## 2) REGISTRY LINE TEMPLATE
`<UID> | <CATEGORY> | <FAMILY> | <STATUS> | <CANON_PATH> | <REF_UID> | <NOTE>`

---

## 3) FAIL CONDITIONS
S0:
- нет UID
- нет записи в registry
- паспорт не в AST дереве

---
END.
