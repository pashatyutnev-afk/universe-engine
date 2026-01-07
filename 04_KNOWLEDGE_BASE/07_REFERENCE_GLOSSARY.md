# REFERENCE GLOSSARY (KB REALM) (CANON)
FILE: 04_KNOWLEDGE_BASE/07_REFERENCE_GLOSSARY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: REALM
REALM: REFERENCE_GLOSSARY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.REALM.GLOSSARY.107
OWNER: SYSTEM
ROLE: KB glossary realm for domain terms (world, narrative, production domain terms as knowledge). Must not duplicate system glossary in STANDARDS without explicit XREF.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MAJOR
- SUMMARY: "Нормализован KB Glossary: Doc Control header + правила no-dup со STANDARDS glossary + формат терминов"
- REASON: "Разделить системные определения и доменные (world) термины"
- IMPACT: "All glossary usage and references"

---

## XREF (UID-first)
XREF: UE.KB.IDX.MASTER.001 | depends_on | KB existence and navigation | 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
XREF: UE.KB.GOV.RULES.011 | governs | no-dup and UID-first | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md
XREF: UE.STD.TERMS.GLOSSARY.400 | references | system glossary (STANDARDS) | 02_STANDARDS/04_TERMS_DEFINITIONS/GLOSSARY.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

## 0) PURPOSE
Этот realm хранит **доменные термины KB**:
- термины мира (внутренние понятия вселенной)
- термины нарратива/ремесла (если доменные, а не системные)
- термины продакшна (если относятся к проекту как знание)

### NO-DUP RULE WITH STANDARDS
Системные определения (про UID, индексы, протоколы и т.п.) живут в STANDARDS Glossary.
KB Glossary не должен копировать их без явного XREF.

---

## 1) TERM ENTRY FORMAT (STANDARD)
Каждый термин оформляется так:

TERM: <Term Name>
- DEFINITION: "<one sentence>"
- DOMAIN: <WORLD|NARRATIVE|CHARACTER|VISUAL|SOUND|PRODUCTION|MARKETING|RESEARCH>
- ALIASES: [<optional>]
- ANTI_DEFINITION: "<what it is NOT>" (optional)
- RELATED: [<optional list of terms>]
- XREF: <optional UID-first links>

---

## 2) CONTROLLED DOMAINS
- WORLD
- NARRATIVE
- CHARACTER
- VISUAL
- SOUND
- PRODUCTION
- MARKETING
- RESEARCH

---

## 3) TERMS LIST (CANON)
> Добавляй термины ниже, в алфавитном порядке (рекомендуется).

### A
- (empty)

### B
- (empty)

### C
- (empty)

### D
- (empty)

### E
- (empty)

### F
- (empty)

### G
- (empty)

### H
- (empty)

### I
- (empty)

### J
- (empty)

### K
- (empty)

### L
- (empty)

### M
- (empty)

### N
- (empty)

### O
- (empty)

### P
- (empty)

### Q
- (empty)

### R
- (empty)

### S
- (empty)

### T
- (empty)

### U
- (empty)

### V
- (empty)

### W
- (empty)

### X
- (empty)

### Y
- (empty)

### Z
- (empty)

---

## 4) LINKING TO ENTITIES (UID-FIRST)
Если термин связан с конкретной сущностью (фракция/технология/концепт):
- лучше сделать эту сущность KB Entity (паспорт + реестр)
- и в термине дать XREF на ENTITY_UID.

Pattern:
XREF:
- XREF: <ENTITY_UID> | references | "term refers to entity" | <passport-path(optional)>

---

## FINAL RULE (LOCK)
KB Glossary хранит доменные термины и не дублирует системный глоссарий STANDARDS без XREF.
--- END.
