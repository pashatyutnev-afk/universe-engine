# 06__KB_RELATION_GRAPH_TEMPLATE.md

SCOPE: Universe Engine (Games volume)
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TEMPLATE
KB_TYPE: GRAPH_ARTIFACT
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.REL_GRAPH.006
OWNER: KB_GOVERNANCE
ROLE: Template for a KB Relation Graph artifact. Provides a stable, auditable way to record REL edges (UID-only) with canonical relation types and rationale.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Introduced relation graph artifact template: edges as UID->UID, canonical REL_TYPE, mandatory WHY, optional tags, and minimal validation checklist."
- REASON: "Need a reusable format to audit relations without mixing NAV links or free-form prose."
- IMPACT: "REL graphs become comparable across modules and can be validated mechanically."
- CHANGE_ID: UE.CHG.2026-01-20.KB.REL_GRAPH.006

---

## 0) PURPOSE (LAW)
Этот шаблон используется для создания отдельного артефакта “RELATION GRAPH”, где связи описаны:
- строго как **UID → UID**,
- только разрешёнными `REL_TYPE`,
- с обязательным `WHY`,
- без URL/RAW в REL.

---

## 1) KB SCOPE (REQUIRED)
KB INPUTS:
- UID источника (FROM_UID)
- UID цели (TO_UID)
- REL_TYPE из канонического словаря
- WHY (рационал)

KB OUTPUTS:
- Таблица/список EDGE записей, пригодный для аудита и валидации

KB BOUNDARIES:
- Этот граф **не** является master-index
- Этот граф **не** задаёт NAV (куда кликать) — только семантические связи
- Этот граф **не** доказывает факты, он фиксирует отношения и их обоснование

KB RAW REFERENCES (IF ANY):
- KB MASTER INDEX:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
- KB RULES:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

---

## 2) ABSOLUTE GRAPH LAWS (BINDING)
### 2.1 UID-only edges
- EDGE записи используют только UID.
- В EDGE запрещены URL/RAW/пути.

### 2.2 Canonical REL_TYPE only
- REL_TYPE обязан быть из канонического словаря типов связей.
- Если нужен новый тип — change-management, иначе нельзя.

### 2.3 Mandatory WHY
- WHY обязателен для каждого ребра.

### 2.4 No silent unknowns
- Если целевой UID неизвестен — использовать `GAP:<...>` (см. раздел 6).

---

## 3) TEMPLATE — GRAPH HEADER (REQUIRED)
Скопируй и заполни:

GRAPH:
- GRAPH_UID: <UE...>
- TITLE: <human readable name>
- SCOPE: <what this graph covers>
- OWNER: <owner>
- STATUS: ACTIVE
- LOCK: FIXED
- VERSION: <x.y.z>
- DATE: <YYYY-MM-DD>
- SOURCE_DOC_UIDS:
  - <UE...>
  - <UE...>

NOTES:
- <optional notes>

---

## 4) TEMPLATE — EDGE TABLE (RECOMMENDED)
Формат таблицы (Markdown):

| EDGE_ID | FROM_UID | REL_TYPE | TO_UID | WHY | TAGS | CONFIDENCE |
|---|---|---|---|---|---|---|
| E001 | UE... | depends_on | UE... | ... | ... | HIGH |

Правила:
- EDGE_ID уникален внутри графа.
- CONFIDENCE: HIGH / MED / LOW (опционально, но полезно для аудита).
- TAGS: список кратких меток (опционально).

---

## 5) TEMPLATE — EDGE LIST (ALTERNATIVE)
Если таблица не подходит, допустим список:

- EDGE_ID: E001
  FROM_UID: UE...
  REL_TYPE: depends_on
  TO_UID: UE...
  WHY: ...
  TAGS: [ ... ]
  CONFIDENCE: HIGH

---

## 6) GAP NOTATION (ALLOWED)
Если цели ещё нет в каноне:

| EDGE_ID | FROM_UID | REL_TYPE | TO_UID | WHY | TAGS | CONFIDENCE |
|---|---|---|---|---|---|---|
| E099 | UE... | depends_on | GAP:UE.KB.... | Need missing module for validation | gap | LOW |

Правила GAP:
- `TO_UID` начинается с `GAP:`
- WHY описывает причину
- TAGS включает `gap`

---

## 7) INTERFACES (RAW-ONLY, OPTIONAL)
Этот граф сам по себе не обязан иметь NAV, но можно указать “куда смотреть”:

- KB MASTER INDEX
  - PURPOSE: Canonical KB entrypoint
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

---

## 8) COMPLIANCE CHECKLIST (REQUIRED)
### 8.1 Edge encoding
- [ ] FROM_UID / TO_UID — только UID (или GAP:UID)
- [ ] REL_TYPE — только из канонического словаря
- [ ] WHY присутствует в каждом EDGE
- [ ] Нет URL/RAW/путей в EDGE

### 8.2 Graph header
- [ ] GRAPH_UID задан
- [ ] VERSION задана
- [ ] SOURCE_DOC_UIDS перечислены (если применимо)

### 8.3 Optional quality
- [ ] CONFIDENCE заполнен там, где есть неопределённость
- [ ] TAGS используются для группировки/поиска

---

## 9) OPTIONAL CHANGE LOG
- 2026-01-20 — CREATE — v1.0.0

---
## END
