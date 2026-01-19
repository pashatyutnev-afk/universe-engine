# SYSTEM ENTITIES REALM — README (CANON)

FILE: 03_SYSTEM_ENTITIES/00__README__SYSTEM_ENTITIES.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: README
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.ALL.DOC.SYSTEM.SYS_ENTITIES_README.001
OWNER: SYSTEM
ROLE: Canonical entry note for the System Entities realm: what lives here, how to navigate it in RAW-only mode, and which documents are authoritative entrypoints.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt README into DOC_CONTROL-compliant format; fixed broken index pointer; added RAW-only navigation contract + authoritative entry links."
- REASON: "Previous README was a single-line stub and referenced a non-existent/incorrect index name, causing navigation loops and user confusion."
- IMPACT: "03_SYSTEM_ENTITIES realm becomes readable and operational: one clear entrypoint set, explicit RAW-only contract, no meta duplication."
- CHANGE_ID: UE.CHG.2026-01-20.SYS_ENTITIES.README.001

---

## 0) PURPOSE (LAW)
Этот README — короткая каноническая записка о слое `03_SYSTEM_ENTITIES`.

Он нужен для:
- объяснения **что такое System Entities** и зачем этот слой существует;
- фиксации **как навигироваться** по сущностям в режиме RAW-only;
- указания **единственных допустимых entrypoints** (правила и индекс слоя).

README не является INDEX и не является RULE: он не заменяет `01__RULES__SYSTEM_ENTITIES.md` и `02__INDEX__SYSTEM_ENTITIES.md`.

---

## 1) WHAT LIVES HERE (SCOPE)
### IN SCOPE
- определения операционных сущностей системы (SPC / ORC / ENG / CTL / VAL / QA / XREF);
- шаблоны сущностей (TPL) и реестры (REG);
- документы правил/индексов, которые делают сущности **операционно используемыми**.

### OUT OF SCOPE
- законы (LAW) — это слой `01_SYSTEM_LAW`;
- стандарты/протоколы системы — это слой `02_STANDARDS`;
- знания (KB) — это слой `04_KNOWLEDGE_BASE`.

---

## 2) NAVIGATION CONTRACT (RAW-ONLY)
Если активирован RAW-only режим:
- переходы выполняются **только** по RAW-ссылкам (никаких угадываний путей);
- для “one-file navigation mode” используются **индексы/реестры**, где RAW перечислены прямо списком;
- если документ/сущность физически существует, но не зарегистрирован/не доступен через operational registry — он “не существует операционно” (для рантайма).

---

## 3) AUTHORITATIVE ENTRYPOINTS (RAW)
Ниже — минимальный набор точек входа именно для этого слоя:

- RULES (как устроены сущности и как ими пользоваться):
  - 03_SYSTEM_ENTITIES/01__RULES__SYSTEM_ENTITIES.md
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01__RULES__SYSTEM_ENTITIES.md

- INDEX (каноническая навигация и/или operational registry режима просмотра):
  - 03_SYSTEM_ENTITIES/02__INDEX__SYSTEM_ENTITIES.md
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/02__INDEX__SYSTEM_ENTITIES.md

- REGISTRIES (общий список реестров слоя):
  - 03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__INDEX_ALL_REGISTRIES.md
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__INDEX_ALL_REGISTRIES.md

- TEMPLATES (общий список шаблонов слоя):
  - 03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/00__INDEX_ALL_TEMPLATES.md
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/00__INDEX_ALL_TEMPLATES.md

---

## 4) OPERATIONAL NOTE (IMPORTANT)
Если ты видишь “зацикливание” на README/RULES — обычно причина одна:
- где-то неверно назван/указан INDEX (например, ссылка на несуществующий `00__INDEX__...` вместо реального `02__INDEX__...`);
- либо INDEX содержит контент не своего типа (смешан RULE/INDEX/registry).

Это лечится строго: RULES остаются RULES, INDEX остаётся INDEX, operational registry — внутри INDEX/REG, без подмены типов.

---

## 5) CHANGE CONTROL (REMINDER)
Любые изменения этого README:
- только через VERSION bump + CHANGE_NOTE + CHANGE_ID;
- LOCK: FIXED (без “финальных правил” внизу — мета живёт только в header).

--- END.
