# 20__WORK_UNITS_STANDARD
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: STANDARD
UID: UE.V2.STD.WORK_UNITS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)

## [M] PURPOSE
Задать универсальный формат единицы работы (WORK_UNIT), чтобы рантайм мог:
- чинить только кусок, а не весь артефакт
- детерминированно ссылаться на место правки без расползания ссылок
- логировать изменения точечно

## [M] DEFINITION
WORK_UNIT = адресуемая часть артефакта, которую можно:
- прочитать отдельно
- изменить отдельно
- валидировать отдельно

## [M] WORK_UNIT ID FORMAT
WORK_UNIT_ID = <SCOPE>:<LOCATOR>

Где:
- SCOPE: LYRICS | DOC | CODE | INDEX | ENTITY | KB | PIPE
- LOCATOR: путь/ключ/секция/блок

## [M] EXAMPLES
### Music
- LYRICS:INTRO
- LYRICS:VERSE_1
- LYRICS:PRECHORUS
- LYRICS:CHORUS
- LYRICS:VERSE_2
- LYRICS:BRIDGE
- LYRICS:OUTRO

### Docs
- DOC:SECTION:KB_SCOPE
- DOC:SECTION:INTERFACES
- DOC:BLOCK:MUST_LOAD_SET

### Code
- CODE:FILE:path/to/app.js::FUNC:handleSubmit
- CODE:FILE:path/to/app.js::BLOCK:ENV_VARS

### Index/Manifest
- INDEX:ENTRY:SPC.MIX_ENGINEER
- INDEX:ENTRY:PIPE.MUSIC.DEFAULT
- INDEX:SELF

## [M] LAW
- Любая правка без указания WORK_UNIT_ID = нарушение, кроме режима FULL_REGEN.
- Любой OUTPUT_PACK обязан иметь карту WORK_UNITS (явно или подразумеваемо структурой).

## [M] GATES
PASS если:
- WORK_UNIT_ID можно однозначно сопоставить месту в артефакте
FAIL если:
- WORK_UNIT_ID не адресуется
