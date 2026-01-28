# QUALITY (QA) — RULES

FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/01__RULES__QA.md
SCOPE: Universe Engine (Games volume) / Quality (QA) / Ruleset
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: RULESET
ENTITY_GROUP: QUALITY (QA)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.DOC.QA.RULES.001
OWNER: SYSTEM
ROLE: Defines QA responsibility, report/issue schema, severity model S0–S3, and ORC gate integration rules.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "DOC CONTROL alignment + normalized issue schema + RAW-only interfaces."
- REASON: "Prevent QA/VAL boundary drift and inconsistent report formats."
- IMPACT: "QA gates become deterministic and auditable."
- CHANGE_ID: UE.CHG.2026-01-20.QA.RULES.001

---

## 0) PURPOSE (LAW)
Этот ruleset определяет:
- что QA оценивает (и чего не делает)
- как оформляется результат (report + issues)
- уровни серьёзности (S0–S3)
- правила использования QA как gate в ORC

## 1) ROLE BOUNDARY (HARD)
QA отвечает за качество восприятия результата.
QA запрещено:
- валидировать структуру по законам (роль VAL)
- принимать доменные решения (роль SPC/ENG)
- менять порядок шагов пайплайна (роль ORC)
- вводить политики исполнения (роль CTL)

Выход за границы роли → S0.

## 2) SEVERITY MODEL (CANON)
Каждый issue обязан иметь `SEVERITY`:
- S0 — STOP. “палево” или критический дефект восприятия, выпуск запрещён.
- S1 — HIGH. заметно большинству, блокирует при строгом gate.
- S2 — MED. снижает качество, желательно исправить.
- S3 — LOW. улучшение/заметка.

## 3) QA MINI-CONTRACT (MANDATORY)
CONSUMES:
- artifact_result: текст/сцена/визуал/аудио/пак результата
- quality_frame: рамки (жанр/тон/контекст/правила подсистемы)

PRODUCES:
- qa_report (PASS/FAIL)
- issues_list (S0–S3)
- fix_suggestions

DEPENDS_ON:
- доменные QA стандарты (если применимо) или []
- базовые системные правила (DOC CONTROL, когда QA используется как promotion gate)

OUTPUT_TARGET:
- OUT | PRJ | LOG (по решению ORC/INTEGRATION_PACKER_SPC)

## 4) REPORT FORMAT (MANDATORY)
QA_REPORT:
- RESULT: PASS | FAIL
- TARGET_UID: <UID цели или NONE>
- SCORE: <0..100> (optional)
- ISSUES:
  - CODE: <short stable code>
  - SEVERITY: S0|S1|S2|S3
  - MESSAGE: "<what is wrong>"
  - FIX_SUGGESTION: "<how to improve>"
- OPTIONAL: RED_FLAGS:
  - "<anti-ai / suspicious patterns>"

## 5) ORC GATE RULE (MANDATORY)
Если шаг ORC имеет `GATE: QA`, то:
- QA обязан вернуть QA_REPORT
- FAIL с S0 всегда блокирует
- S1 блокирует, если ORC не разрешил продолжение
- S2/S3 не блокируют, но фиксируются

## 6) MINIMUM CHECKS (BASELINE)
QA обязан минимум проверить (если применимо к типу результата):
- читаемость/понятность (не “стена текста”, не сломанные структуры)
- ощущение естественности (речь/текст/вокал без “пластика”)
- консистентность тона/жанра
- грубые повтор-паттерны (палево)
- базовая “production readiness” (можно ли показывать/публиковать без стыда)

## 7) INTERFACES (RAW ONLY)
- QA Global Registry (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/02__INDEX_ALL_QA.md
- QA Issue Template:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/00__TEMPLATES/00__TEMPLATE__QA_ISSUE.md
- DOC CONTROL Standard:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- UID Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
