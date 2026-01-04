# ENG ENGINES REALM — LAYER README (CANON REALM)
FILE: 00__README__ENGINES_REALM.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: LAYER_REALM
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: ENG layer borders + meaning + navigation gateway

LOCK: FIXED
OWNER: Universe Engine

---

## 0) WHAT IS ENG (REALM)

ENG — это слой **движков** (Engines): стандартизированные “механизмы мышления/производства”, которые:
- принимают входные артефакты (CONSUMES),
- выполняют преобразование по правилам,
- выдают выходные артефакты (PRODUCES),
- и фиксируют зависимости (DEPENDS_ON).

ENG не хранит “сюжет сам по себе” или “мир сам по себе”.
ENG хранит **методы и процедуры**, по которым эти вещи создаются/валидируются/эволюционируют.

---

## 1) CANON ROOT (PATH)

Канонический корень ENG-слоя:

`03_SYSTEM_ENTITIES/10_ENG__ENGINES/`

---

## 2) ROOT FILES (NAV)

00 — ENG Layer Realm (this file)  
01 — ENG Layer Rules (ruleset): `01__RULES__ENGINES.md`  
02 — ENG Global Index (registry): `02__INDEX_ALL_ENGINES.md`

---

## 3) ABSOLUTE LAW: INDEX IS REALITY

ENG-слой признаёт существование только зарегистрированных движков.

> Если движка нет в `02__INDEX_ALL_ENGINES.md` — для ENG-слоя он **не существует**.  
> Если файл есть, но не зарегистрирован — он **ignored / non-canon**.

---

## 4) WHAT COUNTS AS “ENGINE”

**Engine** — это файл вида:
`NN__<ENGINE_NAME>_ENG.md`

Он обязан иметь:
- шапку (метаданные),
- mini-contract (CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET),
- тело движка (процедура/логика/правила),
- единый STATUS в шапке,
- LOCK в шапке.

**README семейства** — не движок. Это “realm file” семейства:
`00__README__<FAMILY>_ENGINES.md`

---

## 5) FAMILY CONCEPT (ENGINE FAMILIES)

ENG организован семействами (папками). Семейство = область задач/границ.

Формат папки семейства:
`NN_<FAMILY_NAME>_ENGINES`

В каждом семействе:
- `00__README__...` (realm file семейства)
- движки `01..NN__..._ENG.md`

---

## 6) HOW TO USE (WORKFLOW)

1) Открой `02__INDEX_ALL_ENGINES.md`.
2) Найди FAMILY по задаче (TASK → FAMILY MAP).
3) Открой README семейства (realm file) → пойми границы и термины.
4) Иди по движкам **строго по номеру**.
5) Если нужен новый движок:
   - сначала регистрируй его в `02__INDEX_ALL_ENGINES.md`,
   - затем создавай файл,
   - затем прописывай зависимости (DEPENDS_ON) и отражай это в governance.

---

## 7) BOUNDARIES (ANTI-DUPLICATION)

ENG-слой запрещает дубли:
- Если два движка делают одно и то же — это ошибка дизайна.
- Если зона пересечения неизбежна — обязан быть явный “boundary rule” (кто за что отвечает).

Критические границы уже закреплены в INDEX (см. раздел CRITICAL BOUNDARIES).

---

## 8) GOVERNANCE PIPELINE (CHANGES)

Любые изменения состава движков/семейств/версий проходят governance-пайплайн (см. ссылки в INDEX).

Минимально допустимо:
- сначала изменение в INDEX,
- потом изменение файла движка,
- потом фиксация зависимостей,
- потом аудит/лог.

---

## 9) QUICK TEMPLATE: ENGINE MINI-CONTRACT

Обязательный блок в каждом движке:

CONSUMES:
- ...
PRODUCES:
- ...
DEPENDS_ON:
- ...
OUTPUT_TARGET:
- ...

---

## FINAL (LOCK)

ENG Layer Realm — канонические границы слоя ENG.
LOCK: FIXED
