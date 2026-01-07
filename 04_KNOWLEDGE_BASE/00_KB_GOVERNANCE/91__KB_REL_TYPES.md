# KB REL TYPES (SYSTEM)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/91__KB_REL_TYPES

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_SYSTEM
SYSTEM_OBJ: REL_TYPES
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.SYS.REL_TYPES.001
OWNER: SYSTEM
ROLE: Canonical list of allowed relationship types (REL) for KB documents and KB entity passports

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Введён канонический набор REL типов для KB: строгий список + смысл + когда применять"
- REASON: "Без фиксированного словаря REL появляются дубли и несовместимые связи"
- IMPACT: "KB passports, topics XREF/REL, KB registry consistency"

---

## PURPOSE (LAW)
Этот документ — **единственная точка истины** для списка REL типов внутри KB слоя.

Правило:
- REL TYPE обязан быть только из списка ниже.
- Новый REL TYPE добавляется только правкой этого файла (SemVer MINOR/MAJOR).

---

## REL FORMAT (STANDARD)
Запись REL оформляется так:

`REL: <TYPE> -> <TARGET> | WHY:<short>`

Где `<TARGET>` = PATH или UID.

Пример:
`REL: depends_on -> UE.KB.TOPIC.NARR.SCENE_CRAFT.001 | WHY:uses scene model`

---

## CANON REL TYPES (ALLOWED SET)

### 1) depends_on
Смысл: объект A требует объект B для корректной работы/понимания.  
Когда: A без B ломается.

### 2) supports
Смысл: объект B усиливает/поддерживает A, но без него A всё равно работает.  
Когда: B — усилитель/оптимизация.

### 3) part_of
Смысл: A — часть B (иерархия).  
Когда: нужно связать модуль/подтему с большим пакетом.

### 4) related_to
Смысл: есть тематическая связь без зависимости.  
Когда: “рядом по смыслу”.

### 5) xref_to
Смысл: A явно ссылается на B как на источник/подробности (без копирования).  
Когда: вместо дублирования текста.

### 6) produces
Смысл: A производит артефакт/выход B.  
Когда: процесс/метод выдаёт результат.

### 7) consumes
Смысл: A требует вход B (как ресурс/артефакт).  
Когда: процесс/метод принимает на вход.

### 8) replaces
Смысл: A заменяет B (B становится deprecated).  
Когда: миграция смыслов/методов.

### 9) deprecated_by
Смысл: A устарел и заменён B (обратная связь к replaces).  
Когда: оформляем депрекацию.

---

## FORBIDDEN
Запрещено придумывать новые типы на месте.
Если не хватает — расширяем этот файл.

---

## FINAL RULE (LOCK)
Этот документ — SoT по REL типам KB слоя.
--- END.
