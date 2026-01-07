# UNIVERSE ENGINE — UID & MARKING STANDARD (SoT)
FILE: 02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md

SCOPE: Universe Engine / Standards
LEVEL: L0
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Единственная точка истины по маркировкам (UID/ID/STATUS/LOCK/VERSION/PRIORITY/XREF/STORAGE/OUTPUT_TARGET).

---

## 0) PURPOSE
Этот стандарт задаёт единый язык маркировки.
Если правило маркировки не описано здесь — оно не существует.

---

## 1) UNIVERSAL DOCUMENT HEADER (MANDATORY)
Каждый документ обязан иметь в начале:

FILE: <canonical path>
SCOPE: <...>
LEVEL: <L0..L4>
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <x.y>
OWNER: <SYSTEM|HUMAN>
ROLE: <1 line>

---

## 2) UID (MANDATORY FOR ENT/INDEX/PIPELINES)
Формат UID (канон):
UE.<GLOBAL>.<CATEGORY>.<FAMILY>.<NAME>

GLOBAL:
- ENT | STD | IDX | KB | PRJ | OUT | DB | LOG

CATEGORY (только для ENT):
- ENG | ORC | SPC | CTL | VAL | QA

FAMILY: короткий код семейства (NAR/VIS/SND/GOV/GEN/...)
NAME: UPPER_SNAKE_CASE

---

## 3) ID (DOCUMENT SERIAL) — OPTIONAL NOW, CANON LATER
Если включаем серийники документов:
DOC_ID: UE.DOC.<YYYY>.<NNNN>
(пока допускается NONE)

---

## 4) PRIORITY (CANON)
S0 — стоп
S1 — серьёзно
S2 — средне
S3 — мелочь

---

## 5) STORAGE + OUTPUT_TARGET (CANON)
OUTPUT_TARGET:
- KB | PRJ | AST | OUT | LOG

HOME/WORK — определяется проектом (см. STORAGE_MAP в проектах)

---

## 6) XREF (CANON)
Любая ссылка внутри системы должна быть:
- UID (если есть) + raw link (если файл в репо)

Запрещено “ссылка без смысла”.

---

## 7) FINAL LAW
> Управление системой идёт через UID/Marking, а не через догадки и имена файлов.

---
END.
