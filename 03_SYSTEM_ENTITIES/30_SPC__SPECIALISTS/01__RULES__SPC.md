# SPECIALISTS (SPC) — RULESET (LAW) (CANON)

FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01__RULES__SPC.md
SCOPE: Universe Engine (Games volume) / System Entities / Specialists (SPC)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: RULESET
ENTITY_GROUP: SPECIALISTS (SPC)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.SPC.RULES.001
OWNER: SYSTEM
ROLE: Hard rules for SPC layer: intent ownership, packaging law, boundary enforcement, existence registry, and stop behavior.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MAJOR
- SUMMARY: "Rebuilt SPC ruleset: tightened anti-contamination, enforced artifact-only outputs, formalized mini-contract and packaging gates."
- REASON: "Stop drift: SPC mixing ORC/ENG/CTL/VAL/QA duties and emitting naked content."
- IMPACT: "SPC work becomes deterministic and compatible with boot-first runtime."
- CHANGE_ID: UE.CHG.2026-01-20.SPC.RULES.002

---

## 0) CORE LAW
SPC = INTENT + DECISION + PACKAGING owner.

---

## 1) EXISTENCE RULE (ABSOLUTE)
SPC является каноном только если:
- имеет UID
- оформлен по SPC Entity Template
- зарегистрирован в SPC Global Registry (SoT)

---

## 2) SPC MINI-CONTRACT (MANDATORY)
Каждый SPC обязан иметь mini-contract:

SPECIALIZATION_SCOPE:
- what this SPC owns

CONSUMES:
- какие входы ожидаются от ORC/ENG/пользователя

PRODUCES:
- какие артефакты выпускает (как документы)

DEPENDS_ON:
- какие сущности требуются (ORC/ENG/CTL/VAL/QA) или []

OUTPUT_TARGET:
- PRJ | OUT | AST | LOG | KB (если действительно создаётся KB модуль)

---

## 3) OUTPUT ARTIFACT LAW (ABSOLUTE)
FORBIDDEN:
- выдавать результат без документа-артефакта
- писать “просто текст” без схемы/заголовка/версии если это deliverable

MUST:
- использовать шаблон (template) или создать недостающий template через GAP flow
- соблюдать DOC CONTROL header и UID/VERSION правила

---

## 4) BOUNDARY / ANTI-CONTAMINATION (S0)
S0 если SPC:
- задаёт порядок пайплайна вместо ORC
- описывает детерминированный метод вместо ENG (кроме требований/brief)
- вводит политики/лимиты вместо CTL
- объявляет PASS/FAIL по законам вместо VAL
- оценивает качество/естественность вместо QA

---

## 5) PACKAGING GATES (FAST)
G0 — Header Gate:
- DOC CONTROL header корректен
- STATUS/LOCK один раз, валидные значения

G1 — Contract Gate:
- mini-contract конкретный (CONSUMES/PRODUCES не “вода”)

G2 — Artifact Gate:
- deliverable оформлен документом-артефактом
- если шаблон нужен — он применён или создан (GAP закрыт)

G3 — Interface Gate:
- навигационные ссылки RAW-only
- без угадывания путей

FAIL любого gate:
- S0 если ломает навигацию/контракт
- иначе S1/S2 по контексту задачи (фиксируется в blockers/issue)

---

## 6) GOVERNANCE SPECIALISTS PRIORITY (LAW)
Если есть конфликт решения:
- governance SPC имеет приоритет над доменным SPC.

Governance SPC финализирует:
- упаковку результата
- соответствие стандартам
- корректность ссылок и структуры deliverable.

---

## 7) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- компетентностные методички, чеклисты, эталоны

KB OUTPUTS:
- только если PRODUCES содержит KB module artifact (иначе none)

BOUNDARIES:
- SPC не заменяет KB памятью переписки.

---

## 8) INTERFACES (RAW ONLY)
- SPC REALM README:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__README__SPC_REALM.md
- SPC GLOBAL REGISTRY (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md
- SPC CREATE FLOW:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03__CREATE_FLOW__SPC.md
- SPC ENTITY TEMPLATE:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__TEMPLATES/00__TEMPLATE__SPC_ENTITY.md
- SPC OUTPUT PACK TEMPLATE:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__TEMPLATES/00__TEMPLATE__SPC_OUTPUT_PACK.md

--- END.
