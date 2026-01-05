# ENG CORE ENGINE — TEMPLATE
FILE: NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 01_CORE_ENGINES
CLASS: CORE (L1)
ENGINE_ID: ENG.CORE.NN.<ENGINE_NAME>
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: <one-line purpose of this core engine>

---

## 0) PURPOSE (LAW)

Коротко:
- что формирует/фиксирует этот движок в ядре
- какой core-invariant он держит

---

## 1) CORE INVARIANTS (MANDATORY)

Этот движок гарантирует:
- INVARIANT_1: <описание>
- INVARIANT_2: <описание>
- INVARIANT_3: <описание>

---

## 2) WHEN TO USE (TRIGGERS)

Используй когда:
- [ ] условие 1
- [ ] условие 2
- [ ] условие 3

Не используй когда:
- [ ] это governance кейс (иди в 00_GOVERNANCE_ENGINES)
- [ ] это domain/production кейс

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <TYPE_1>
- <TYPE_2>
- <TYPE_3>

PRODUCES:
- <TYPE_1>
- <TYPE_2>
- <TYPE_3>

DEPENDS_ON:
- []  # или список вида: [ENG.GOV.04.CHANGE_CONTROL]

OUTPUT_TARGET:
- <куда склады смотреть результат>

---

## 4) STATE MODEL (IF APPLICABLE)

Если движок про состояние:
- STATE VARIABLES: <список>
- VALID VALUES: <ограничения>
- TRANSITIONS: <переходы/условия>

---

## 5) PROCESS (HOW IT WORKS)

1) Validate input
2) Normalize / classify
3) Update / generate core artifact
4) Record transition (если был)
5) Output snapshot

---

## 6) FAILURE MODES

- Failure 1 → симптом → фикс
- Failure 2 → симптом → фикс

---

## 7) CHECKLIST (FAST RUN)

- [ ] Invariants written
- [ ] Mini-contract present
- [ ] Dependencies declared (если есть)
- [ ] Output target defined
- [ ] Raw link present

---

## 8) RAW LINK (MANDATORY)

🔗 RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/NN__<ENGINE_NAME>_ENG.md

---

OWNER: Universe Engine
LOCK: OPEN
