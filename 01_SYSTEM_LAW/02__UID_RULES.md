# UNIVERSE ENGINE — UID RULES (LAW)
FILE: 01_SYSTEM_LAW/02__UID_RULES.md

SCOPE: Universe Engine
LAYER: SYSTEM LAW
LEVEL: L0
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Закон UID. Фиксирует обязательность UID, принципы уникальности/неизменяемости и правила использования UID во всех слоях.

---

## 0) PURPOSE
UID нужен чтобы:
- ссылаться на элементы без двусмысленности
- связывать сущности/процессы/артефакты без “догадок”
- иметь стабильный идентификатор, независимый от путей и названий файлов

---

## 1) UID IS MANDATORY (CORE LAW)
UID обязателен для:
- всех ENT (ENG/ORC/SPC/CTL/VAL/QA)
- всех канонических реестров (INDEX_ALL_* и master indexes)
- всех “выпущенных” стандартов (SoT документов)

Если ENT/SoT документ без UID — он считается incomplete и не может быть “истиной”.

---

## 2) UID UNIQUENESS + IMMUTABILITY (ABSOLUTE)
### 2.1 Uniqueness
> UID уникален во всей системе.

Запрещено:
- два разных элемента с одним UID
- “временные UID”

### 2.2 Immutability
> UID не переименовывается.

Если смысл элемента изменился настолько, что UID “не подходит”:
- создаётся новый UID
- старый переводится в deprecated (через индекс/протокол)

---

## 3) UID ≠ FILE PATH
UID не равен пути файла.

- путь может меняться при рефакторинге
- UID должен оставаться ключом связи

---

## 4) UID REGISTRATION LAW (EXISTENCE)
UID действителен только если:
1) элемент зарегистрирован в соответствующем INDEX/реестре
2) у элемента есть корректная шапка (STATUS/LOCK/VERSION/OWNER/ROLE)
3) UID не конфликтует с уже существующим UID

UID без регистрации в индексе считается invalid / non-canon.

---

## 5) UID AS PRIMARY REFERENCE
В чатах, логах, спорных местах, зависимостях и проблемах:
- сначала указывается UID
- потом (опционально) имя файла/путь/ссылка

Формулировка проблем обязана ссылаться на UID:
> “Проблема в UE.ENT.ORC.PRD.SCENE_PIPELINE”

---

## 6) UID IN DEPENDENCIES (NO HIDDEN LINKS)
Любая зависимость должна фиксироваться через UID:
- DEPENDS_ON обязателен (или [])
- скрытые зависимости запрещены

---

## 7) UID STANDARD LOCATION (SoT)
Детальные форматы UID и правила сегментов определяются стандартом (SoT):

- `02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md`

Этот LAW файл задаёт только обязательность и принципы применения (без дублирования форматов).

---

## 8) FINAL LAW
> Система управляется UID, а не именами и догадками.  
> Нет UID + нет регистрации = элемент не существует.

OWNER: Universe Engine  
LOCK: FIXED

---
END.
