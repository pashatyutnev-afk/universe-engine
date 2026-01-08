# GOVERNANCE ENGINES — README TEMPLATE (ETALON)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__TEMPLATE__README__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE_README
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.ENG.GOV.TPL.README.001
OWNER: SYSTEM
ROLE: Canonical README template for ENG families. Enforces family boundaries, navigation, and governance compatibility.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Etalon family README template: strict header + family law + engine listing skeleton + dependency/xref + governance pipeline hooks."
- REASON: "Stop drift across families; unify navigation and boundaries."
- IMPACT: "All ENG families become consistent and index-compatible."
- CHANGE_ID: UE.CHG.2026-01-08.GOV.TPL.README.001

---

## 0) HOW TO USE THIS TEMPLATE (LAW)

1) Создай/открой README семьи:
   `03_SYSTEM_ENTITIES/10_ENG__ENGINES/<FAMILY_FOLDER>/00__README__<FAMILY_NAME>_ENGINES.md`
2) Полностью скопируй этот шаблон.
3) Замени все `TODO:` и удали строки `TEMPLATE NOTE:`.
4) Вставь raw-links:
   - на README семьи (этот файл)
   - на шаблон движка семьи
   - на шаблон README семьи (если хранишь)
5) Вставь список движков строго по номеру, строго по каноническим путям.
6) Проверь совместимость с глобальным индексом `02__INDEX_ALL_ENGINES.md`.

TEMPLATE NOTE:
- README семьи — это “realm law” и “navigation map” для движков семейства.
- README семьи не описывает весь Universe Engine, только границы этой семьи.

---

# <FAMILY NAME> — ENGINES REALM (CANON)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/<FAMILY_FOLDER>/00__README__<FAMILY_NAME>_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: README_REALM
FAMILY: <FAMILY_FOLDER>
CLASS: <GOVERNANCE|CORE|DOMAIN|EXPRESSION|STYLE|PRODUCTION|SOUND|META>
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 0.1.0
UID: UE.ENG.<FAMILY_KEY>.README.001
OWNER: <OWNER_ROLE_OR_SYSTEM>
ROLE: Realm law + boundaries + navigation for <FAMILY_FOLDER> engines.

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<what is affected>"
- CHANGE_ID: UE.CHG.YYYY-MM-DD.<TAG>.<NNN>

---

## 1) PURPOSE (LAW)

TODO: Одно предложение: зачем существует это семейство, какой “тип задач” оно покрывает.

---

## 2) FAMILY BOUNDARIES (ANTI-DUPLICATION LAW)

### 2.1 WHAT THIS FAMILY OWNS
TODO (5–10 пунктов):
- ...
- ...

### 2.2 WHAT THIS FAMILY DOES NOT OWN
TODO (5–10 пунктов):
- ...
- ...

### 2.3 HARD BOUNDARY NOTES (must be explicit)
TODO: Укажи 2–5 пар “похожие вещи, но это НЕ сюда”.
Example style:
- “X belongs to <other family/engine>, not here.”

Hard rule:
- Если граница не прописана — семья будет конфликтовать с другими.

---

## 3) FAMILY NAVIGATION (ORDER LAW)

### 3.1 Canon order inside this family
Правило:
- Движки читаются и применяются строго по номеру `01..NN`.
- README (`00`) — не движок.

### 3.2 Engine naming standard
- Folder: `NN_<FAMILY_NAME>_ENGINES`
- Engine file: `NN__<ENGINE_NAME>_ENG.md`
- README file: `00__README__<FAMILY_NAME>_ENGINES.md`

Hard rule:
- Номер в названии файла = номер в индексе.

---

## 4) TEMPLATES (MANDATORY)

ENGINE TEMPLATE (raw-link):
TODO: https://raw.githubusercontent.com/<...>/03_SYSTEM_ENTITIES/10_ENG__ENGINES/<FAMILY_FOLDER>/00__TEMPLATE__ENGINE__<FAMILY_NAME>_ENGINES.md

README TEMPLATE (raw-link):
TODO: https://raw.githubusercontent.com/<...>/03_SYSTEM_ENTITIES/10_ENG__ENGINES/<FAMILY_FOLDER>/00__TEMPLATE__README__<FAMILY_NAME>_ENGINES.md

Hard rule:
- Без указания шаблонов семья считается incomplete.

---

## 5) THIS FAMILY ENGINES (CANON LIST)

TEMPLATE NOTE:
- Здесь должен быть список всех движков семейства, строго по номеру.
- Каждый пункт: `NN — Title — raw-link`.

01 — TODO Engine Name — 🔗 TODO(raw-link)  
02 — TODO Engine Name — 🔗 TODO(raw-link)  
03 — TODO Engine Name — 🔗 TODO(raw-link)  
...  
NN — TODO Engine Name — 🔗 TODO(raw-link)

---

## 6) MINI-CONTRACT STANDARD (FAMILY LAW)

Каждый движок этой семьи обязан содержать mini-contract:

- CONSUMES:
- PRODUCES:
- DEPENDS_ON:
- OUTPUT_TARGET:

Hard rule:
- Если mini-contract отсутствует — движок считается incomplete и не может быть каноном.

---

## 7) DEPENDENCY + XREF HOOKS (NO HIDDEN DEPS)

### 7.1 Dependency registry owner
TODO (raw-link to dependency registry engine if governance-family exists):
- Recommended: `00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG`

### 7.2 Dependency record line standard
`<FAMILY>/<ENGINE_A> -> <FAMILY>/<ENGINE_B> | TYPE:<HARD|SOFT> | WHY:<short reason>`

### 7.3 Cross-layer xref (if applicable)
TODO:
- Links to XREF maps if the family must interface with ORC/SPC/CTL/VAL/QA.

Hard rule:
- Зависимости должны быть явные (DEPENDS_ON + registry record).

---

## 8) GOVERNANCE PIPELINE COMPATIBILITY (MANDATORY)

Если эта семья влияет на канон, индексы, статусы, версии, или структуру, то действует правило:

- Любая правка канонических индексов/порядка/состава семьи
  обязана проходить governance pipeline.

Recommended hooks:
- Audit log engine (фиксировать изменения)
- Change control engine (правки/релизы)
- Canon authority engine (кто имеет право)
- Versioning & memory engine (как помним версии)

TEMPLATE NOTE:
- Для не-governance семей, тут просто ссылки/правила “как семья взаимодействует”.

---

## 9) QUALITY BAR (FAMILY STANDARD)

Минимальный стандарт качества для движков семьи:

- Deterministic procedure (повторяемость)
- Explicit gates (PASS/WARN/FAIL/BLOCKED)
- Severity (S0–S3) и actions required
- Examples (good/bad) + edge cases
- No hidden dependencies
- Clear storage targets

Hard rule:
- Движок без examples не считается эталонным.

---

## 10) COMMON COLLISIONS (ANTI-CONFLICT MAP)

TODO: Список 3–7 типичных конфликтов с другими семьями и как их избежать.
Format:
- Collision: <with what> → Resolution: <where it belongs> → Reason: <short>

---

## 11) CHANGE RULES (READ THIS BEFORE EDIT)

### 11.1 Allowed STATUS (strict set)
- STATUS: DRAFT
- STATUS: ACTIVE
- STATUS: DEPRECATED
- STATUS: ARCHIVED

### 11.2 LOCK (strict set)
- LOCK: OPEN
- LOCK: FIXED

### 11.3 Audit enforcement (if canon-impacting)
TODO:
- Как фиксируется правка (куда запись, какой формат, какой CHANGE_ID).

Hard rule:
- Дубли STATUS/LOCK внизу файла запрещены.

---

## 12) QUICK LINKS (OPTIONAL)

- Global ENG Index: TODO (raw-link to 02__INDEX_ALL_ENGINES.md)
- Family folder path: `03_SYSTEM_ENTITIES/10_ENG__ENGINES/<FAMILY_FOLDER>/`
- Templates: (engine + readme)
- Dependency registry: TODO
- Audit log: TODO

---

## FINAL RULE (LOCK)

> Этот README — realm law семьи.  
> Он задаёт границы, порядок и правила совместимости.  
> Любая правка, влияющая на канон, проходит governance pipeline.

OWNER: <OWNER_ROLE_OR_SYSTEM>
LOCK: <OPEN|FIXED>
