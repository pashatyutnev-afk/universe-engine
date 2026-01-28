# VALIDATORS (VAL) — RULES

FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/01__RULES__VAL.md
SCOPE: Universe Engine (Games volume) / Validators (VAL) / Ruleset
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: RULESET
ENTITY_GROUP: VALIDATORS (VAL)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.DOC.VAL.RULES.001
OWNER: SYSTEM
ROLE: Defines VAL responsibility, report/violation schema, severity model S0–S3, and ORC gate integration rules.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "DOC CONTROL alignment + normalized report schema + RAW-only interfaces."
- REASON: "Remove legacy spec pointers and prevent mixed-role contamination."
- IMPACT: "VAL checks become deterministic and auditable."
- CHANGE_ID: UE.CHG.2026-01-20.VAL.RULES.001

---

## 0) PURPOSE (LAW)
Этот ruleset определяет:
- что VAL обязан проверять (и чего не делает)
- как оформляется результат (report + violations)
- какие уровни серьёзности используются (S0–S3)
- как VAL подключается в ORC как обязательный gate

## 1) ROLE BOUNDARY (HARD)
VAL отвечает за compliance законам и стандартам.
VAL запрещено:
- улучшать художественное качество (роль QA)
- принимать доменные решения (роль SPC/ENG)
- менять маршрут/порядок шагов (роль ORC)
- вводить политики исполнения (роль CTL)

Если VAL выходит за границы роли → нарушение S0 (role contamination).

## 2) SEVERITY MODEL (CANON)
Каждое нарушение обязано иметь `SEVERITY`:
- S0 — STOP. Артефакт считается невалидным, пайплайн должен остановиться.
- S1 — HIGH. Блокирует, если ORC не разрешил продолжение.
- S2 — MED. Не блокирует, но требует исправления.
- S3 — LOW. Улучшение/заметка.

## 3) VAL MINI-CONTRACT (MANDATORY)
CONSUMES:
- artifact(s): документы/артефакты, которые нужно проверить
- governing_refs: законы/стандарты/индексы, которые задают требования

PRODUCES:
- validation_report (PASS/FAIL)
- violations_list (S0–S3)
- fix_actions (обязательные изменения)

DEPENDS_ON:
- DOC CONTROL standard
- UID rules
- naming rules
- index structure spec
- (опционально) доменные стандарты, если проверяется доменный пакет

OUTPUT_TARGET:
- OUT | PRJ | LOG (по решению ORC/INTEGRATION_PACKER_SPC)

## 4) REPORT FORMAT (MANDATORY)
VAL_REPORT:
- RESULT: PASS | FAIL
- TARGET_UID: <UID цели или NONE>
- VIOLATIONS:
  - CODE: <short stable code>
  - SEVERITY: S0|S1|S2|S3
  - MESSAGE: "<что нарушено>"
  - FIX_ACTION: "<что сделать>"
  - OPTIONAL: AUTO_FIX_SUGGESTION: "<идея, но не решение за домен>"

## 5) ORC GATE RULE (MANDATORY)
Если шаг ORC имеет `GATE: VAL`, то:
- VAL обязан вернуть VAL_REPORT
- FAIL с S0 всегда блокирует
- S1 блокирует, если ORC step не содержит явного разрешения продолжать при S1
- S2/S3 не блокируют, но фиксируются

## 6) MINIMUM CHECKS (BASELINE)
VAL обязан минимум проверить:
- DOC CONTROL header: обязательные поля есть, значения допустимы
- отсутствие дублирования метаданных в теле
- корректность RAW ссылок (если требуются): формат + отсутствие угадывания
- соответствие index/registry дисциплине (если документ заявлен как SoT)
- соответствие UID/CHANGE_ID формату (если документ canon)

## 7) INTERFACES (RAW ONLY)
- DOC CONTROL Standard:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- UID Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- Naming Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md
- Index Structure Spec:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/09__INDEX_STRUCTURE_SPEC.md
- VAL Global Registry (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/02__INDEX_ALL_VALIDATORS.md
