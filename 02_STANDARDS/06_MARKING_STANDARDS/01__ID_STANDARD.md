# ID STANDARD — GLOBAL
FILE: 02_STANDARDS/06_MARKING_STANDARDS/01__ID_STANDARD.md

SCOPE: Universe Engine / System
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Единый стандарт идентификаторов (ID) для всех объектов системы и проектов.

SOURCE OF TRUTH:
- Формат ID и правила валидности описаны здесь.

---

## 0) CORE LAW
- Если объект не имеет валидного ID — он считается INVALID.
- ID должен быть уникальным в пределах системы.
- ID не меняется задним числом. Если нужно переименование — создаётся новый ID + XREF (renamed_from).

---

## 1) ID FORMAT (CANON)
`<PREFIX>:<TYPE>:<NAME>[:<SCOPE>][:vNN]`

Где:
- PREFIX — класс объекта (ENT/ART/DB/LOG/SPC/ENG/ORC/CTL/VAL/QA/TPL/STD)
- TYPE — тип объекта внутри класса (SCENE, CHR, PACK, SCENE_STACK…)
- NAME — стабильный ключ (latin, digits, underscore)
- SCOPE — опционально (например EP01, PROJ_AWM)
- vNN — версия для артефактов/ассетов (v01, v02…)

---

## 2) NAME RULES
- Allowed: `a-z A-Z 0-9 _ -`
- No spaces, no Cyrillic in ID
- Рекомендуемый стиль: NAME = `snake_case`

---

## 3) REQUIRED CLASSES (MINIMUM)
### 3.1 Entities (ENT)
Формат: `ENT:<TYPE>:<NAME>`
Примеры:
- `ENT:CHR:vita`
- `ENT:LOC:river_bank`
- `ENT:PACK:ep01`
- `ENT:SCENE:ep01_scn_003`
- `ENT:SHOT:ep01_scn_003_sh_02`
- `ENT:FORM:ethr_ghost`

### 3.2 Artifacts (ART)
Формат: `ART:<TYPE>:<NAME>:<SCOPE>:vNN`
Примеры:
- `ART:SCENE_STACK:ep01_scn_003:EP01:v01`
- `ART:SHOTLIST:ep01_scn_003:EP01:v01`
- `ART:AUDIO_CUES:ep01_scn_003:EP01:v01`

### 3.3 Standards / Templates / DB / Logs
- `STD:<TYPE>:<NAME>`
- `TPL:<TYPE>:<NAME>`
- `DB:<TYPE>:<NAME>`
- `LOG:<TYPE>:<NAME>`

---

## 4) COLLISION RULE
- Два разных объекта не могут иметь одинаковый ID.
- Проверка коллизий входит в DOC_CONTROL (см. 08__DOC_CONTROL.md).

---

## 5) XREF RULE
Любая связь должна ссылаться на ID (см. 05__REL_POLICY_XREF.md).

---
END.
