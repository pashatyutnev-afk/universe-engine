# XREF — CREATE / UPDATE FLOW (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__CREATE_FLOW__XREF.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: RUNBOOK
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.RUNBOOK.CREATE_FLOW.001
OWNER: SYSTEM
ROLE: Deterministic procedure to add or update XREF maps safely.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Created runbook for XREF updates: schema-first, anti-dup, version bumps, gates."
- REASON: "Prevent accidental drift while expanding system."
- IMPACT: "XREF maintenance becomes repeatable and auditable."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.RUNBOOK.001

---

## 0) PURPOSE (LAW)
Этот RUNBOOK описывает, как безопасно добавлять/обновлять XREF карты.

---

## 1) INPUTS (MINIMUM)
- intent: что добавляем (ENG→ORC / ORC→SPC / validation / pipelines)
- target file: какой MAP документ
- new rows: новые записи или изменение существующих
- reason + impact (1–2 строки)

---

## 2) PROCEDURE (MANDATORY ORDER)
1) SELECT MAP
- выбери нужный MAP файл по типу соответствия.

2) SCHEMA CHECK
- убедись, что все обязательные поля присутствуют.

3) ANTI-DUP CHECK
- проверь, что запись не дублирует существующую связь (same key).

4) APPLY CHANGE
- добавь/обнови строку(и).

5) VERSION BUMP + CHANGE_NOTE
- bump VERSION в заголовке (PATCH/MINOR по масштабу).
- обнови CHANGE_NOTE (summary/reason/impact/change_id).

6) DOC-CONTROL READY
- форма, поля, табличность, отсутствие мусора.

7) UPDATE REALM INDEX (IF NEEDED)
- если добавился новый файл в реалме — обнови `00__INDEX__CROSSREF.md` (только список+назначение).

---

## 3) OUTPUT
- updated MAP file(s)
- optionally updated realm index
- short “what changed” note (если требуется для пакета поставки)

--- END.
