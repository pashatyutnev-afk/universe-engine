# VALIDATORS (VAL) — REALM README

FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/00__README__VALIDATORS_REALM.md
SCOPE: Universe Engine (Games volume) / System Entities / Validators (VAL)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: README (REALM)
ENTITY_GROUP: VALIDATORS (VAL)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.DOC.VAL.REALM.001
OWNER: SYSTEM
ROLE: Defines VAL realm boundaries, responsibilities, outputs, and integration points (RAW-only navigation compatible).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "DOC CONTROL alignment: fixed FILE mismatch, normalized header, removed legacy SoT pointers, added RAW-only interfaces + scope discipline."
- REASON: "Prevent drift and broken navigation in VAL realm docs."
- IMPACT: "VAL realm becomes auditable and compatible with boot-first + RAW-only runtime."
- CHANGE_ID: UE.CHG.2026-01-20.VAL.REALM.001

---

## 0) PURPOSE (LAW)
Этот README задаёт рамки слоя `50_VAL__VALIDATORS`:
- кто такой VAL и где его границы
- какие типы артефактов VAL выпускает
- как VAL подключается как gate в пайплайны ORC
- какие документы являются входами и выходами в рамках слоя

## 1) SCOPE
Применяется ко всем семействам и файлам внутри:
- `03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/**`

Этот README не является SoT для существования файлов. SoT для NAV/EXISTENCE в слое VAL — глобальный индекс:
- `03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/02__INDEX_ALL_VALIDATORS.md`

## 2) ROLE BOUNDARIES
### 2.1 VAL OWNS
VAL отвечает за проверку соответствия законам и стандартам системы:
- корректность DOC CONTROL (header, отсутствие дублированных метаданных, структура)
- корректность UID / VERSION / STATUS / LOCK (по законам)
- корректность RAW-only навигации (без угадывания путей)
- корректность правил существования (index/registry дисциплина)
- фиксацию нарушений (S0–S3) и требований к исправлению

### 2.2 VAL DOES NOT OWN
VAL не принимает решения, которые принадлежат другим классам:
- не оценивает художественное качество и естественность (это QA)
- не принимает смысловые/творческие решения (это SPC/ENG)
- не управляет порядком шагов пайплайна (это ORC)
- не устанавливает политики/лимиты исполнения (это CTL)

## 3) OUTPUTS (WHAT VAL PRODUCES)
VAL выпускает только проверочные артефакты и требования к исправлениям:
- `VALIDATION_REPORT` (PASS/FAIL)
- `VIOLATIONS_LIST` (S0–S3)
- `FIX_ACTIONS` (что именно нужно изменить)
- `OPTIONAL: AUTO_FIX_SUGGESTIONS` (только предложения, не “решение” за домен)

## 4) INTEGRATION (HOW VAL IS USED)
### 4.1 ORC Gate rule (high-level)
Если ORC step помечен `GATE: VAL`, то:
- VAL обязан вернуть PASS/FAIL
- FAIL с S0 всегда блокирует пайплайн
- S1 блокирует, если ORC не разрешил продолжение
- S2/S3 не блокируют, но фиксируются как требования/улучшения

## 5) MINIMUM FILE SET (REALM)
Минимальный состав слоя VAL:
- realm README (этот файл)
- ruleset
- global registry (index)
- create flow
- templates (минимум: сущность валидатора + запись нарушения)

## 6) INTERFACES (RAW ONLY)
- VAL Global Registry (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/02__INDEX_ALL_VALIDATORS.md
- VAL Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/01__RULES__VAL.md
- DOC CONTROL Standard:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- UID Rules (LAW):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md

## 7) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- system laws + standards required for validation (DOC CONTROL, UID, naming, index model)

KB OUTPUTS:
- none (VAL outputs are reports/violations, not KB modules)

BOUNDARIES:
- VAL не создаёт новые знания о домене, только проверяет соответствие правилам и фиксирует нарушения
