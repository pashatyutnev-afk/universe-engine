# PRJ CREATE FLOW — BOOTSTRAP (PACK → EP → SCENE → SHOT)
FILE: 05_PROJECTS/00_PRJ_GOVERNANCE/07__PRJ_CREATE_FLOW.md

SCOPE: Universe Engine / Projects Workflow
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Каноническая процедура создания PRJ объектов без ошибок. Регистрирует существование через PRJ Registry.

SOURCE OF TRUTH:
- PRJ Rules: `05_PROJECTS/00_PRJ_GOVERNANCE/01__RULES__PRJ.md`
- PRJ Registry: `05_PROJECTS/00_PRJ_GOVERNANCE/02__INDEX__PRJ_GLOBAL_REGISTRY.md`
- PRJ Storage: `05_PROJECTS/00_PRJ_GOVERNANCE/04__PRJ_STORAGE_MAP.md`
- PRJ Template: `05_PROJECTS/00_PRJ_GOVERNANCE/06__TEMPLATE__PRJ_PASSPORT.md`
- Scene Link Law: `05_PROJECTS/00_PRJ_GOVERNANCE/05__SCENE_LINK_LAW.md`

---

## 0) CORE LAW
PRJ объект считается существующим только после:
(1) создания паспорта + (2) записи в PRJ Global Registry.

---

## 1) CREATE PACK (once per production pack)
### Steps
1) Определи FAMILY (обычно GEN)
2) Сгенерируй UID:
   `UE.PRJ.PACK.<FAMILY>.<PACK_NAME>`
3) Создай папку:
   `05_PROJECTS/01_PACKS/<PACK_UID>/`
4) Создай паспорт:
   `05_PROJECTS/01_PACKS/<PACK_UID>/00__PACK__PASSPORT.md`
   (по шаблону PRJ PASSPORT)
5) Добавь строку в PRJ Registry

### Registry line template
`<UID> | PACK | <FAMILY> | <STATUS> | <CANON_PATH> | NONE | <NOTE>`

---

## 2) CREATE EP (inside PACK)
### Steps
1) UID:
   `UE.PRJ.EP.<FAMILY>.EP01` (или другое имя)
2) Создай папку:
   `.../<PACK_UID>/01_EPISODES/<EP_UID>/`
3) Создай паспорт:
   `.../<EP_UID>/00__EP__PASSPORT.md`
4) В паспорте:
   PACK_REF: `<PACK_UID>`
5) Запиши в PRJ Registry

### Registry line template
`<EP_UID> | EP | <FAMILY> | <STATUS> | <CANON_PATH> | <PACK_UID> | <NOTE>`

---

## 3) CREATE SCENE (inside EP)
### Steps
1) UID:
   `UE.PRJ.SCENE.<FAMILY>.EP01_SCN_003`
2) Создай папку:
   `.../<EP_UID>/01_SCENES/<SCENE_UID>/`
3) Создай паспорт:
   `.../<SCENE_UID>/00__SCENE__PASSPORT.md`
4) В паспорте:
   PACK_REF: `<PACK_UID>`
   EP_REF: `<EP_UID>`
   OUTPUT_TARGETS: (пока можно TBD)
   STACK_REF: `TBD`
5) Запиши в PRJ Registry

### Registry line template
`<SCENE_UID> | SCENE | <FAMILY> | <STATUS> | <CANON_PATH> | <EP_UID> | <NOTE>`

---

## 4) CREATE SHOT (optional, inside SCENE)
### Steps
1) UID:
   `UE.PRJ.SHOT.<FAMILY>.EP01_SCN_003_SH_012`
2) Создай папку:
   `.../<SCENE_UID>/01_SHOTS/<SHOT_UID>/`
3) Паспорт:
   `.../<SHOT_UID>/00__SHOT__PASSPORT.md`
4) В паспорте:
   SCENE_REF: `<SCENE_UID>`
5) Запиши в PRJ Registry

---

## 5) AFTER STACK EXISTS (mandatory update)
Когда создан STACK в OUT:
- вернись в паспорт SCENE и замени:
  STACK_REF: `<STACK_UID>`
- обнови OUTPUT_TARGETS если нужно

---

## 6) FAIL CONDITIONS
S0:
- нет UID
- нет записи в PRJ Registry
- неправильный CANON_PATH
- SCENE без EP_REF
S1:
- SCENE без STACK_REF после того как STACK уже существует

---
END.
