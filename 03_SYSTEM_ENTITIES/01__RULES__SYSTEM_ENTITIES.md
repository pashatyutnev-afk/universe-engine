# SYSTEM ENTITIES — RULESET (LAW) — CANON
FILE: 03_SYSTEM_ENTITIES/01__RULES__SYSTEM_ENTITIES.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: RULESET
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENT.RULES.SYSTEM_ENTITIES.001
OWNER: SYSTEM
ROLE: Hard rules + existence + RAW-only navigation + invocation discipline for all system entity realms (REG/TPL/ENG/ORC/SPC/CTL/VAL/QA/XREF).

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: MAJOR
- SUMMARY: "Created missing System Entities ruleset to unblock BOOT and enforce deterministic entity execution."
- REASON: "BOOT requires this file; empty file breaks marker confirmation and allows non-deterministic behavior."
- IMPACT: "Entity layer becomes auditable: existence + RAW-only + SPC-first + stop conditions."
- CHANGE_ID: UE.CHG.2026-01-19.ENT.RULES.001

---

## 0) PURPOSE (LAW)
Этот RULESET фиксирует обязательные правила для слоя `03_SYSTEM_ENTITIES`:
- что считается “существующим” (existence rule)
- как навигировать (RAW-only)
- как запускать работу (SPC-first)
- какие стоп-условия допустимы

---

## 1) DEFINITIONS (STRICT)
- ENTITY REALM: семейство сущностей (REG/TPL/ENG/ORC/SPC/CTL/VAL/QA/XREF).
- OPERATIONAL INDEX: индекс/реестр, который является источником RAW-ссылок для вызова сущностей.
- MARKER: узнаваемая строка/заголовок в открытом RAW файле, подтверждающий его реальность.
- NON-EXISTENT: файл есть “где-то”, но нет RAW-ссылки в оперативном индексе текущего рантайма → использовать запрещено.

---

## 2) HARD RULES (ABSOLUTE)

### R1 — EXISTENCE RULE (ABSOLUTE)
Сущность/шаблон/реестр считается существующим в рантайме только если:
- на него есть RAW-ссылка в оперативной базе ссылок (ROOT snapshot и/или явно присланные RAW ссылки),
- и при открытии файла подтверждён marker.

FORBIDDEN:
- использовать “видел в дереве папок” как доказательство существования,
- строить ссылку руками (no guessing).

### R2 — RAW-ONLY NAVIGATION (ABSOLUTE)
Любая навигация по сущностям выполняется только RAW ссылками.

FORBIDDEN:
- github.com UI ссылки как навигация,
- PATH как механизм (PATH допускается только как метка).

### R3 — SPC-FIRST EXECUTION (ABSOLUTE)
Любая задача исполняется строго:
Lead SPC → (0–3 Support SPC) → (optional) ORC/ENG/CTL/VAL/QA → Packaging → Signoff.

FORBIDDEN:
- начинать с ENG/ORC/CTL/VAL/QA без Lead SPC.

### R4 — DOC CONTROL HEADER (MANDATORY)
Любой канонический документ сущности обязан иметь единый header с полями:
FILE/SCOPE/LAYER/DOC_TYPE/LEVEL/STATUS/LOCK/VERSION/UID/OWNER/ROLE/CHANGE_NOTE.

FORBIDDEN:
- дублировать STATUS/LOCK/UID/VERSION/OWNER/ROLE в теле/в конце.

### R5 — NAMING & NUMBERING (MANDATORY)
Имена файлов/папок должны соответствовать `01_SYSTEM_LAW/01__NAMING_RULES.md`.
Номер в списках/индексах должен совпадать с `NN__` в имени файла.

### R6 — TEMPLATE-FIRST FOR NEW ARTIFACTS (MANDATORY)
Если требуется новый документ/сущность:
- сначала определяется TEMPLATE (или создаётся TEMPLATE),
- затем создаётся документ по TEMPLATE.

FORBIDDEN:
- “голый контент” без артефакт-документа.

### R7 — STOP CONDITIONS (ONLY THESE)
Рантайм обязан остановиться только по причинам:
- RAW missing
- marker not confirmed
- input absent

---

## 3) OPERATIONAL COMPLIANCE NOTICE (MANDATORY)
Если система не может открыть RAW или подтвердить marker:
- она обязана явно сообщить о причине,
- и не имеет права продолжать выполнение “по памяти/логике/догадке”.

---

## 4) REFERENCES (RAW ONLY)
(вставь сюда 1–3 ключевые RAW ссылки на протокол SPC-first/RAW-only и глобальные индексы, если хочешь жёстко связать правила; сами ссылки должны быть из твоего ROOT snapshot)

--- END
