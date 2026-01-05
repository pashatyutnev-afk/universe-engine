# ENG GOVERNANCE ENGINE — TEMPLATE
FILE: NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
ENGINE_ID: ENG.GOV.NN.<ENGINE_NAME>
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
ROLE: <one-line purpose of this governance engine>

---

## 0) PURPOSE (LAW)

Коротко и жёстко:
- что этот движок делает
- что он гарантирует системе
- какую боль закрывает

---

## 1) WHEN TO USE (TRIGGERS)

Используй движок когда:
- [ ] условие 1
- [ ] условие 2
- [ ] условие 3

Не используй когда:
- [ ] условие A (это другой движок/слой)
- [ ] условие B

---

## 2) INPUT CONTRACT (CONSUMES)

CONSUMES:
- <TYPE_1> — кратко что это
- <TYPE_2>
- <TYPE_3>
- <TYPE_4>
- <TYPE_5>

---

## 3) OUTPUT CONTRACT (PRODUCES)

PRODUCES:
- <TYPE_1> — кратко что выходит
- <TYPE_2>
- <TYPE_3>
- <TYPE_4>
- <TYPE_5>

OUTPUT_TARGET:
- <where the outputs must be stored / which folder / which registry file>

---

## 4) DEPENDENCIES (MANDATORY)

DEPENDS_ON:
- []  # либо список: [ENG.GOV.XX.YYYY, ENG.CORE.XX.ZZZZ]

XREF:
- Dependency registry entry required: YES/NO
- If YES: `06__DEPENDENCY_REGISTRY_ENG.md`

---

## 5) PROCESS (HOW IT WORKS)

Шаги как алгоритм (коротко, но однозначно):

1) Input validation (что проверяем на входе)
2) Classification (как определить тип кейса)
3) Action (что меняем/фиксируем)
4) Logging (что пишем в audit)
5) Result (что считается “done”)

---

## 6) RULES ENFORCED (WHAT IT MAKES ILLEGAL)

Этот движок делает незаконным:
- правило 1
- правило 2
- правило 3

---

## 7) FAILURE MODES (WHAT CAN GO WRONG)

- Failure 1 → симптом → что делать
- Failure 2 → симптом → что делать

---

## 8) MINI-CHECKLIST (FAST RUN)

- [ ] Input types correct
- [ ] Dependencies declared
- [ ] Audit entry created (if change)
- [ ] Version memory updated (if rules)
- [ ] Index updated (if adds/removes engines)

---

## 9) RAW LINK (MANDATORY)

🔗 RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/NN__<ENGINE_NAME>_ENG.md

---

OWNER: Universe Engine
LOCK: OPEN
