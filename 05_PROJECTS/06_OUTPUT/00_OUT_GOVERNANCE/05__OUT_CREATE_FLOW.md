# OUT CREATE FLOW — BOOTSTRAP (STACK / SCRIPT / AUDIO / VIDEO / IMAGE)
FILE: 06_OUTPUT/00_OUT_GOVERNANCE/05__OUT_CREATE_FLOW.md

SCOPE: Universe Engine / Output Workflow
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Каноническая процедура создания OUT объектов без ошибок. Регистрирует существование через OUT Registry.

SOURCE OF TRUTH:
- OUT Registry: `06_OUTPUT/00_OUT_GOVERNANCE/01__INDEX__OUT_GLOBAL_REGISTRY.md`
- OUT Storage: `06_OUTPUT/00_OUT_GOVERNANCE/03__OUT_STORAGE_MAP.md`
- OUT Template: `06_OUTPUT/00_OUT_GOVERNANCE/04__TEMPLATE__OUT_PASSPORT.md`
- Scene Stack Standard: `02_STANDARDS/06_MARKING_STANDARDS/06__SCENE_STACK_4TRACK.md`
- Scene Link Law: `05_PROJECTS/00_PRJ_GOVERNANCE/05__SCENE_LINK_LAW.md`

---

## 0) CORE LAW
OUT объект считается существующим только после:
(1) создания паспорта/файла + (2) записи в OUT Global Registry.

---

## 1) CREATE STACK (mandatory for every SCENE)
### Steps
1) Возьми SCENE_UID: `UE.PRJ.SCENE...`
2) Сгенерируй STACK_UID:
   `UE.OUT.STACK.<FAMILY>.<SCENE_KEY>_4TRACK`
   где SCENE_KEY = имя сцены (например EP01_SCN_003)
3) Создай файл:
   `06_OUTPUT/01_STACKS/<STACK_UID>.md`
4) Заполни по OUT PASSPORT:
   REF_UID: `<SCENE_UID>`
   CATEGORY: STACK
   TRACKS: A/B/C/D (пустые допустимы)
5) Запиши в OUT Registry
6) Вернись в PRJ SCENE паспорт и проставь STACK_REF: `<STACK_UID>`

### Registry line template
`<STACK_UID> | STACK | <FAMILY> | <STATUS> | 06_OUTPUT/01_STACKS/<STACK_UID>.md | <SCENE_UID> | 4track stack`

---

## 2) CREATE SCRIPT (optional but recommended)
UID:
`UE.OUT.SCRIPT.<FAMILY>.<SCENE_KEY>_SCRIPT`

Файл:
`06_OUTPUT/02_SCRIPTS/<UID>.md`

REF_UID:
SCENE_UID или EP_UID (как укажешь)

---

## 3) CREATE AUDIO (optional)
UID:
`UE.OUT.AUDIO.<FAMILY>.<SCENE_KEY>_AUDIO`

Файл:
`06_OUTPUT/03_AUDIO/<UID>.md`

---

## 4) CREATE VIDEO (optional)
UID:
`UE.OUT.VIDEO.<FAMILY>.<SCENE_KEY>_VIDEO`

Файл:
`06_OUTPUT/04_VIDEO/<UID>.md`

---

## 5) CREATE IMAGE (optional)
UID:
`UE.OUT.IMAGE.<FAMILY>.<SCENE_KEY>_IMG_001` (если серия кадров)

Файл:
`06_OUTPUT/05_IMAGES/<UID>.md`

---

## 6) FAIL CONDITIONS
S0:
- нет UID
- нет записи в OUT Registry
- нет REF_UID
- STACK без 4 дорожек
S1:
- SCENE не обновлён STACK_REF после создания STACK

---
END.
