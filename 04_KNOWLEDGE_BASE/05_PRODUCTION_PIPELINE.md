# PRODUCTION PIPELINE (KB REALM) (CANON)
FILE: 04_KNOWLEDGE_BASE/05_PRODUCTION_PIPELINE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: REALM
REALM: PRODUCTION_PIPELINE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.REALM.PRODUCTION.105
OWNER: SYSTEM
ROLE: Knowledge realm for production pipeline: stages, handoffs, artifact expectations, QA gates, version discipline, and pipeline patterns. Knowledge only; assets and outputs live outside KB.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MAJOR
- SUMMARY: "Нормализован realm Production: Doc Control header + каркас стадий/артефактов/QA + UID-first linking"
- REASON: "Чтобы продакшн работал как процесс, а KB оставалась знанием"
- IMPACT: "All production knowledge placement"

---

## XREF (UID-first)
XREF: UE.KB.IDX.MASTER.001 | depends_on | KB existence and navigation | 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
XREF: UE.KB.GOV.RULES.011 | governs | KB boundaries and no-dup | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md
XREF: UE.STD.SPEC.DOC_CONTROL.103 | references | doc control discipline | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
XREF: UE.LAW.VERSIONING.003 | references | SemVer change policy | 01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
XREF: UE.STD.SPEC.NAT_GATES.106 | references | quality gates framing | 02_STANDARDS/01_SPECIFICATIONS/06__NATURALNESS_GATES_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

## 0) PURPOSE
Этот realm хранит **методики продакшна**:
- этапы пайплайна
- какие артефакты на выходе каждого этапа
- как делаются handoffs
- какие QA-гейты и проверки
- как управлять версиями/изменениями

Realm не хранит выходные видео/аудио/рендеры и рабочие файлы.
KB хранит знание, а не файлы.

---

## 1) STAGES (PIPELINE MAP)
> Это общий каркас. Конкретика может жить в проектных слоях, но правила — здесь.

S0 — Intent / Brief
S1 — Outline / Scene Pack
S2 — Script / Dialogue
S3 — Previs / Visual Plan
S4 — Production (assets/work)
S5 — Post (edit, sound, grade)
S6 — Release / Distribution
S7 — Archive

---

## 2) ARTIFACT CONTRACTS (WHAT EACH STAGE PRODUCES)
Для каждого stage фиксируем:
- входы (inputs)
- выходы (outputs)
- критерии готовности (done definition)

Пример формата:
STAGE: S1 (Outline/Scene Pack)
- INPUTS: <list>
- OUTPUTS: <list>
- DONE_WHEN: <criteria>
- QA: <checks>

---

## 3) HANDOFF RULES
- handoff = проверяемый переход ответственности
- handoff запрещён без “done definition”
- handoff должен оставлять ссылки (UID-first) на ключевые сущности/сцены/доки

---

## 4) QA GATES (QUALITY SYSTEM)
- NAT gates (если применимо)
- continuity checks
- technical checks (format, naming, registry compliance)
- review protocol (кто и что смотрит)

---

## 5) VERSION DISCIPLINE (PRACTICAL)
- версии документов = SemVer (если канон)
- изменения канона проходят через Canon Protocol
- “тихие правки” запрещены в канонических артефактах

---

## 6) PIPELINE FAILURE MODES (ANTI-PATTERNS)
- перескакивание стадий без выходных артефактов
- “работает у меня локально” без фиксированных артефактов
- хранение продакшн-файлов в KB
- дубли правил (no-dup violation)

---

## 7) LINKING TO ENTITIES / SCENES (UID-FIRST)
Если пайплайн ссылается на:
- сущность → ENTITY_UID
- сцену/ивент → SCENE_UID/EVENT_UID (если заведены)
- доки → DOC_UID (если канонические)

Pattern:
XREF:
- XREF: <TARGET_UID> | references | "pipeline usage" | <path(optional)>

---

## 8) EXAMPLES / PLAYBOOKS (OPTIONAL)
> Примеры пайплайна под конкретные сезоны/форматы.
> Внутренние ссылки — UID-first.

---

## 9) OPEN QUESTIONS / TODO (OPTIONAL)
- (list)

--- END.
