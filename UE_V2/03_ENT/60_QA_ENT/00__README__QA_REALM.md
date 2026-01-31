# QUALITY (QA) — REALM README

FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/00__README__QA_REALM.md
SCOPE: Universe Engine (Games volume) / System Entities / Quality (QA)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: README (REALM)
ENTITY_GROUP: QUALITY (QA)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.DOC.QA.REALM.001
OWNER: SYSTEM
ROLE: Defines QA realm boundaries, outputs, and how QA gates protect usability and production readiness (distinct from VAL legality).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "DOC CONTROL alignment: normalized header + boundaries + RAW-only interfaces."
- REASON: "Prevent drift and mixed responsibilities between QA/VAL/SPC."
- IMPACT: "QA realm becomes auditable and consistent with runtime gates."
- CHANGE_ID: UE.CHG.2026-01-20.QA.REALM.001

---

## 0) PURPOSE (LAW)
QA отвечает за качество восприятия результата:
- naturalness / human-likeness
- консистентность (тон, стиль, “как звучит/чувствуется”)
- анти-ИИ сигнатуры (палево шаблонов, “пластик”, повторяемые паттерны)
- производственная готовность (короткие тесты восприятия, пригодность к выпуску)

QA не является SoT для существования файлов. SoT для NAV/EXISTENCE в слое QA:
- `03_SYSTEM_ENTITIES/60_QA__QUALITY/02__INDEX_ALL_QA.md`

## 1) SCOPE
Применяется ко всем семействам и файлам внутри:
- `03_SYSTEM_ENTITIES/60_QA__QUALITY/**`

## 2) ROLE BOUNDARIES
### 2.1 QA OWNS
- оценка качества результата (включая “палево ИИ”)
- отчёт PASS/FAIL и список issues
- рекомендации по улучшению (без доменных решений)

### 2.2 QA DOES NOT OWN
QA запрещено:
- валидировать формальную структуру по законам (это VAL)
- принимать смысловые/доменные решения (это SPC/ENG)
- управлять пайплайном (это ORC)
- задавать политики/лимиты исполнения (это CTL)

Нарушение границ роли → S0 (role contamination).

## 3) OUTPUTS (WHAT QA PRODUCES)
- `QA_REPORT` (PASS/FAIL, опционально SCORE 0..100)
- `ISSUES_LIST` (S0–S3)
- `FIX_SUGGESTIONS`
- `OPTIONAL: RED_FLAGS` (признаки “палево ИИ”)

## 4) INTEGRATION (HOW QA IS USED)
Если ORC step помечен `GATE: QA`, то:
- QA обязан вернуть PASS/FAIL
- FAIL с S0 всегда блокирует
- S1 блокирует, если ORC не разрешил продолжение
- S2/S3 не блокируют, но фиксируются

## 5) MINIMUM FILE SET (REALM)
- realm README (этот файл)
- ruleset
- global registry (index)
- create flow
- templates (минимум: сущность QA + issue запись + qa-check template)

## 6) INTERFACES (RAW ONLY)
- QA Global Registry (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/02__INDEX_ALL_QA.md
- QA Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/01__RULES__QA.md
- DOC CONTROL Standard:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- UID Rules (LAW):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md

## 7) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- quality gates standards (domain-specific), plus system-level laws/standards when QA is used as a promotion gate

KB OUTPUTS:
- none (QA outputs are reports/issues, not KB modules)

BOUNDARIES:
- QA не создаёт новый канон домена, только оценивает качество результата и готовность к выпуску
