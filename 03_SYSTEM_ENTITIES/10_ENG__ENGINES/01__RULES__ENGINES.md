# ENG ENGINES — RULESET (LAYER RULES)
FILE: 01__RULES__ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
RULESET_TYPE: ENG_LAYER_RULES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Mandatory rules for ENG engines — naming, contracts, links, locks, registry compliance

---

## 0) ABSOLUTE LAWS

### 0.1 Registry law
> Любой ENG-движок обязан быть зарегистрирован в `02__INDEX_ALL_ENGINES.md`.  
> Иначе он non-canon.

### 0.2 Mini-contract law
> У каждого движка обязан быть блок MINI-CONTRACT:  
CONSUMES / PRODUCES / DEPENDS_ON / OUTPUT_TARGET

---

## 1) NAMING + NUMBERING (MANDATORY)

### 1.1 Family folder naming
`NN_<FAMILY_NAME>_ENGINES`

### 1.2 Engine file naming
`NN__<ENGINE_NAME>_ENG.md`  
Нумерация внутри семейства начинается с `01`.

### 1.3 Family README naming
`00__README__<FAMILY>_ENGINES.md`

---

## 2) LINK STANDARD (MANDATORY)

- Каждый движок должен иметь прямой raw-link в INDEX.
- Каждый FAMILY README должен иметь raw-link в INDEX.
- Заглушки “список без изменений” запрещены.

---

## 3) STATUS + LOCK (MANDATORY)

- В шапке файла ровно один `STATUS: ...`
- В конце файла **не допускается** второй `STATUS: ...`
- LOCK только:
  - `LOCK: OPEN`
  - `LOCK: FIXED`

---

## 4) DEPENDENCY LAW

- Все зависимости обязаны быть в `DEPENDS_ON`
- Зависимости обязаны отражаться в dependency registry:
  `00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md`

---

OWNER: Universe Engine  
LOCK: FIXED
