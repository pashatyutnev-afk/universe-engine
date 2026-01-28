# SYSTEM ENTITIES REALM — README (CANON)

FILE: 03_SYSTEM_ENTITIES/00__README__SYSTEM_ENTITIES.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: README
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.ENT.README.SYS_ENTITIES.001
OWNER: SYSTEM
ROLE: Human-first entry to the Entities layer. Explains what entities are, how this layer is structured, where the canonical RULES and INDEX live, and how to navigate in RAW-only mode.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt README into strict entry guide: no type mixing, explicit entry links, RAW-only reading contract, and quick routing to RULES/INDEX."
- REASON: "Users were stuck in loops and confusion between README/RULE/INDEX."
- IMPACT: "Layer becomes readable in one pass and routes correctly to operational laws and registries."
- CHANGE_ID: UE.CHG.2026-01-20.SYS_ENTITIES.README.001

---

## 0) PURPOSE (WHAT IS THIS)
`03_SYSTEM_ENTITIES` — это слой **операционных сущностей** Universe Engine.

Сущности — это “исполнители” и “контролёры” системы:
- кто принимает решения (SPC),
- кто задаёт пайплайн (ORC),
- кто выполняет детерминированную логику (ENG),
- кто блокирует/ограничивает (CTL),
- кто валидирует (VAL),
- кто принимает по качеству (QA),
- кто хранит карты соответствий (XREF),
- плюс служебные реестры (REG) и шаблоны (TPL).

Этот README:
- **объясняет** как устроен слой,
- **показывает** куда идти за правилами и индексом,
- **не заменяет** RULES и INDEX.

---

## 1) CANON ENTRYPOINTS (READ FIRST)
В этом слое есть три канонических “входа”. Начинай всегда с них:

1) README (этот файл)  
- объясняет слой и маршрутизацию

2) RULES (правила слоя, что считается сущностью и как она становится operationally real)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01__RULES__SYSTEM_ENTITIES.md

3) INDEX (канонический реестр состава слоя: что существует и где лежит)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/02__INDEX__SYSTEM_ENTITIES.md

---

## 2) RAW-ONLY NAVIGATION CONTRACT
Если включён RAW-only режим:
- навигация делается **только по RAW ссылкам**;
- запрещено угадывать пути и имена файлов;
- любые “операционные переходы” должны быть возможны через копирование RAW ссылки.

Практика чтения:
- открываешь INDEX слоя,
- находишь нужный объект,
- копируешь RAW и переходишь.

---

## 3) OPERATIONAL REALITY (IMPORTANT)
Ключевая идея слоя:

**Операционно реальным** считается только то, что зарегистрировано в `02__INDEX__SYSTEM_ENTITIES.md`.

Если файл физически есть в репозитории, но его нет в INDEX слоя:
- он считается NON-OPERATIONAL / ignored,
- его нельзя использовать как доказанную сущность.

Подробно — в RULES слоя:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01__RULES__SYSTEM_ENTITIES.md

---

## 4) STRUCTURE (WHAT LIVES WHERE)
Верхний уровень слоя организован по классам сущностей:

- `00_REG__REGISTRIES/` — реестры (журналы, deprecation, changelog, registry индексы)
- `01_TPL__TEMPLATES/` — шаблоны для создания сущностей/документов слоя
- `10_ENG__ENGINES/` — ENG сущности (детерминированная логика)
- `20_ORC__ORCHESTRATORS/` — ORC сущности (пайплайны и handoffs)
- `30_SPC__SPECIALISTS/` — SPC сущности (намерение, решения, упаковка результата)
- `40_CTL__CONTROLLERS/` — CTL сущности (ограничения, блокировки, политики)
- `50_VAL__VALIDATORS/` — VAL сущности (валидация и нарушения)
- `60_QA__QUALITY/` — QA сущности (гейты качества)
- `90_XREF__CROSSREF/` — XREF сущности (карты соответствий, матрицы)

Конкретный состав файлов — всегда через INDEX слоя:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/02__INDEX__SYSTEM_ENTITIES.md

---

## 5) WHAT TO DO NEXT (QUICK ROUTES)
Если тебе нужно:

### A) “Понять правила сущностей и запреты”
Иди в RULES:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01__RULES__SYSTEM_ENTITIES.md

### B) “Найти конкретную сущность и открыть её”
Иди в INDEX и бери RAW:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/02__INDEX__SYSTEM_ENTITIES.md

### C) “Создать новую сущность”
Общий принцип:
- берёшь TEMPLATE из `01_TPL__TEMPLATES/`,
- создаёшь файл в правильном классе,
- регистрируешь в INDEX слоя (иначе non-operational).

---

## 6) COMMON FAILURE MODES (WHY PEOPLE GET STUCK)
- **Петля README/RULE/INDEX**: когда README начинает “быть индексом” или “быть правилами”.
- **Фантомные сущности**: файл есть, но не зарегистрирован в INDEX слоя.
- **Угадывание путей**: попытка “догадаться где лежит сущность” вместо RAW ссылки из индекса.
- **Смешивание типов**: RULE документ начинает превращаться в список файлов, а INDEX — в правила.

---

## 7) CHANGE CONTROL REMINDER
Любое изменение в этом слое должно быть:
- с обновлением VERSION (semver),
- с CHANGE_NOTE (что/почему/impact/change_id),
- без дублирования метаданных в теле.

--- END.
