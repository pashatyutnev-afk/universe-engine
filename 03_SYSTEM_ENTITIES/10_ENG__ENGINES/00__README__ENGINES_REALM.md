# ENG ENGINES — LAYER REALM (ROOT)
FILE: 00__README__ENGINES_REALM.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
REALM_TYPE: ENG_LAYER_REALM
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Root realm for ENG layer — defines what ENG is, how engines are structured, and where canon lives

---

## 0) WHAT IS ENG (DEFINITION)

ENG (Engines) — это **набор канонических движков** Universe Engine.  
Движок = документ с правилами/процессом, который:
- принимает входы (CONSUMES),
- выдаёт выход (PRODUCES),
- имеет зависимости (DEPENDS_ON),
- имеет назначение результата (OUTPUT_TARGET).

---

## 1) ENG LAYER ROOT FILES (MANDATORY)

00 — ENG Layer Realm (this file)  
01 — ENG Layer Rules — `01__RULES__ENGINES.md`  
02 — Global ENG Registry (Index) — `02__INDEX_ALL_ENGINES.md`

---

## 2) DIRECTORY REALM (CANON PATH)

Все ENG файлы живут строго здесь:

`03_SYSTEM_ENTITIES/10_ENG__ENGINES/`

Семейства (FAMILIES) — это папки внутри этого каталога.

---

## 3) NAMING LAW (MANDATORY)

### 3.1 Family folder
Формат: `NN_<FAMILY_NAME>_ENGINES`

Пример: `00_GOVERNANCE_ENGINES`

### 3.2 Engine file
Формат: `NN__<ENGINE_NAME>_ENG.md`

Пример: `04__CHANGE_CONTROL_ENG.md`

### 3.3 Family README (Realm file)
README не является движком. Всегда номер `00`:

`00__README__<FAMILY>_ENGINES.md`

---

## 4) CANON EXISTENCE RULE (ABSOLUTE)

> Если движка нет в `02__INDEX_ALL_ENGINES.md` — он **не существует** для ENG слоя.  
> Если файл существует, но не зарегистрирован — он **ignored / non-canon**.

---

## 5) STATUS + LOCK (STANDARD)

В шапке каждого файла допускается **один** `STATUS: ...`.

Фиксация:
- `LOCK: OPEN` — документ в разработке
- `LOCK: FIXED` — канонически закреплён (любые правки идут через governance pipeline)

---

## 6) GOVERNANCE PIPELINE (MANDATORY)

Любая правка ENG-канона проходит:
- `00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`
- `00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md`
- `00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md`
- `00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md`

---

OWNER: Universe Engine  
LOCK: FIXED
