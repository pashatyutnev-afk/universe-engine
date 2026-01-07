# DOC REGISTRY STANDARD (SoT)
FILE: 02_STANDARDS/01_SPECIFICATIONS/07__DOC_REGISTRY_STANDARD.md

SCOPE: Universe Engine / Standards
LEVEL: L0
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Стандарт серийной нумерации документов и ведения реестра (1 строка = 1 документ). Используется как “память/доказательная база”.

REFERENCES:
- Marking SoT: `02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md`
- Doc Control: `02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md`
- Storage Map: `02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md`

---

## 1) CORE LAW
Каждый документ, который считается “выпущенным в систему”, обязан быть записан в DOC REGISTRY.

---

## 2) DOC_ID FORMAT (CANON)
DOC_ID — серийный номер документа:

UE.DOC.<YYYY>.<NNNN>

Где:
- YYYY — год выпуска (2026…)
- NNNN — сквозной номер в рамках года (0001, 0002, ...)

Пример:
UE.DOC.2026.0007

---

## 3) WHEN ASSIGNED
DOC_ID присваивается в момент, когда документ:
- готов для добавления в канон/базу
- или используется как артефакт в пайплайне

Черновики без DOC_ID допустимы.

---

## 4) REGISTRY ROW FORMAT (MANDATORY)
Одна строка:

DOC_ID | DATE(YYYY-MM-DD) | TITLE | TYPE | OWNER | STATUS | LOCK | FILE_PATH | UID(if any) | OUTPUT_TARGET | NOTE

TYPE:
- STD | ENT | IDX | KB | PRJ | OUT | LOG | OTHER

---

## 5) FINAL LAW
> Нет записи в реестре — нет документа в системе (для целей памяти/доказательств).

---
END.
