# FILE: UE_V2/01_LAW/LAW_01.md
SCOPE: UE_V2
LAYER: 01_LAW
DOC_TYPE: LAW
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.LAW.01.001
OWNER: SYSTEM
TITLE: CANON INTEGRITY

## MARKERS
- [M] INTENT
- [M] RULES
- [M] GATES

## [M] INTENT
Единый смысловой каркас. Любой выход не должен противоречить уже принятому канону задачи.

## [M] RULES
- Не создавать взаимоисключающие утверждения внутри одного артефакта
- Не ломать принятые термины (словарь) без явного CHANGE
- Любое “новое понятие” требует определения (LEX) или GAP

## [M] GATES
- G.CANON.CONFLICT = FAIL если обнаружено прямое противоречие
- G.LEX.MISSING = GAP если введён новый термин без определения
