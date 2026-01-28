# 26__ENTITY_ADDRESS_LINE_FMT

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: STD
UID: UE.V2.STD.ENTITY_ADDRESS_LINE_FMT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Формат ADDRESS LINE для сущностей: чтобы без кликов было ясно кто это, где живёт, как запускается, куда передаёт, что производит.

---

## [M] INTENT
Сделать каждую сущность "адресной карточкой", чтобы:
- ассистент не блуждал
- люди понимали роль сущности с одного экрана
- ORC мог быстро понять входы/выходы/передачи

---

## [M] ADDRESS LINE (CANON TEMPLATE)
ADDRESS_LINE:
- REALM: (ORC|CTL|VAL|QA|SPC|ENG|XREF|REG|KB)
- DOMAIN: (CORE|MUSIC|VIS|LOR|REL|...)
- FAMILY: (например TRACK_BUILD / FOCUS_LOOP / RELEASE_PACK / GOVERNANCE)
- ENTRY: (YES|NO)  // можно ли запускать напрямую
- DEFAULT_PIPE: (например PIPE_MUSIC_TRACK)  // если применимо
- STAGES: (csv стадий где участвует, например S2_PLAN,S6_REVIEW)
- IO_IN: (csv IO types)
- IO_OUT: (csv IO types)
- HANDOFF_TO: (csv ROLE/UID или "CTL->VAL->QA->PACK")
- SCOPE_GATE: (KB_SCOPE_ID)  // что разрешено брать из KB
- INDEX_REF: (путь на 00__INDEX_* реалма)
- NOTES: (1 строка)

---

## [M] RULES
1) ADDRESS_LINE обязателен для сущностей ORC/CTL/VAL/QA/SPC/ENG.
2) ADDRESS_LINE не заменяет RAW ссылки, но даёт понимание "куда и как".
3) ENTRY=YES означает: эту сущность можно выбрать как DEFAULT_ORC или явный вызов.
4) SCOPE_GATE обязателен (кроме bootstrap-ядра).
5) IO_IN/IO_OUT должны соответствовать STD/19__IO_TYPES.
6) Если FAMILY не определена — использовать "GENERAL".

---

## [M] MIN REQUIRED SECTIONS IN ENTITY (for consistency)
- паспорт (UID/ROLE/DOMAIN/CAP/STATUS/VERSION)
- ADDRESS_LINE (по шаблону)
- INTERFACES (IO + requires + incompat)
- ACTIONS (шаги, коротко)
- HANDOFFS (кому передаёт)
- GATES (PASS/REWORK/GAP/STOP)

---

## [M] GATES
PASS если:
- ADDRESS_LINE заполнен и совпадает со смыслом сущности
REWORK если:
- нет IO/SCOPE/HANDOFF, и сущность непонятно как использовать
