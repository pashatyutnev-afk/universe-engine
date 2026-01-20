# ORCHESTRATORS (ORC) — RULES

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01__RULES__ORC.md
SCOPE: Universe Engine (Games volume) / Orchestrators (ORC) / Ruleset
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: RULESET
ENTITY_GROUP: ORCHESTRATORS (ORC)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.DOC.ORC.RULES.001
OWNER: SYSTEM
ROLE: Canon rules for ORC entities: pipeline contract, step schema, gate discipline, handoff policy, and role-boundary enforcement.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "DOC CONTROL alignment + removed legacy UID spec pointers + normalized ORC mini-contract + step schema + gate ordering rule."
- REASON: "Prevent incomplete ORC files and mixed schemas."
- IMPACT: "ORC becomes deterministic and auditable for runtime routing."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.RULES.001

---

## 0) CORE LAW
ORC отвечает только за:
- ORDER (порядок шагов)
- ROUTING (кто выполняет шаг)
- INPUT/OUTPUT (что нужно и что считается результатом)
- HANDOFF_TARGETS (куда кладём результат)
- GATES (CTL/VAL/QA точки)

ORC НЕ делает:
- доменные решения (SPC/ENG)
- формальные проверки законов (VAL)
- оценку качества/естественности (QA)
- политики/лимиты (CTL)
- хранение контента (KB/PRJ/AST/OUT)

Нарушение границ роли → S0.

## 1) EXISTENCE RULE (ABSOLUTE)
ORC существует в каноне только если:
- имеет UID (по UID rules)
- зарегистрирован в ORC Global Registry (SoT)
- файл оформлен по ORC Entity Template (минимум: contract + pipeline steps + gates)

Если файл есть в репо, но не зарегистрирован — NON-CANON.

## 2) ORC MINI-CONTRACT (MANDATORY)
Каждый ORC обязан содержать MINI-CONTRACT:

CONSUMES:
- список входов (1..N), строго именованных
  пример: TASK_TEXT, ROOT_LINK_BASE, OPTIONAL_LINKS, TARGET_ARTIFACT_TYPE

PRODUCES:
- список выходов (1..N)
  пример: PIPELINE_PLAN, ROUTING_MAP, CHECKPOINTS, HANDOFF_TARGETS

DEPENDS_ON:
- список сущностей-исполнителей (SPC/ENG/CTL/VAL/QA) или []

OUTPUT_TARGET:
- PRJ | OUT | AST | LOG (минимум один)

Отсутствие mini-contract → S0 (incomplete ORC).

## 3) PIPELINE STEP SCHEMA (MANDATORY)
Каждый ORC имеет список STEPS, где каждый STEP обязан иметь поля:

STEP_ID: <01..NN>
NAME: <human-readable>
EXECUTOR_UID: <RAW UID or canonical executor ref>
CONSUMES: [<1..N inputs>]
PRODUCES: [<1..N outputs>]
GATE: <NONE | CTL | VAL | QA | CTL+VAL | CTL+QA | VAL+QA | CTL+VAL+QA>
FAIL_SEVERITY: <S0|S1|S2|S3>
HANDOFF_TARGET: <KB|PRJ|OUT|AST|LOG|DB|NONE>
NOTES: "<optional>"

Если поле отсутствует → S0 (broken step schema).

## 4) GATE DISCIPLINE (MANDATORY)
Если GATE включает несколько типов, порядок проверки по умолчанию:
1) CTL (policy/limits)
2) VAL (formal compliance)
3) QA (quality)

Если требуется другой порядок — ORC обязан явно указать это в NOTES шага.

## 5) HANDOFF LAW (MANDATORY)
ORC обязан явно указать:
- куда кладётся промежуточный результат (если он должен быть сохранён)
- куда кладётся финальный результат

Запрещено “умолчанием” оставлять место хранения, если результат должен быть найден повторно.

## 6) FAIL POLICY (CANON)
- S0: стоп пайплайна
- S1: блокирует, если pipeline step не разрешает продолжение при S1
- S2: не блокирует, но фиксируется как требование к исправлению
- S3: заметка/улучшение

ORC обязан указывать FAIL_SEVERITY на каждом шаге.

## 7) ANTI-CONFLICT RULE (S0)
Если ORC:
- пишет контент вместо SPC/ENG
- валидирует вместо VAL
- оценивает качество вместо QA
- вводит политики вместо CTL
то это S0: role contamination.

## 8) INTERFACES (RAW ONLY)
- ORC Global Registry (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/02__INDEX_ALL_ORCHESTRATORS.md
- ORC Create Flow:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/03__ORC_CREATE_FLOW.md
- ORC Entity Template:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__ORC_ENTITY.md
- ORC Step Template:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__ORC_PIPELINE_STEP.md
