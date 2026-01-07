# MARKETING & DISTRIBUTION (KB REALM) (CANON)
FILE: 04_KNOWLEDGE_BASE/06_MARKETING_DISTRIBUTION.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: REALM
REALM: MARKETING_DISTRIBUTION
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.REALM.MARKETING.106
OWNER: SYSTEM
ROLE: Knowledge realm for marketing and distribution: positioning, messaging, audience models, channel strategy, release planning, content funnel, and measurement. Knowledge only; not a campaign asset folder.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MAJOR
- SUMMARY: "Нормализован realm Marketing: Doc Control header + каркас позиционирования/каналов/релизов/метрик + UID-first linking"
- REASON: "Маркетинг должен быть описан как система, а не разрозненные заметки"
- IMPACT: "All marketing knowledge placement"

---

## XREF (UID-first)
XREF: UE.KB.IDX.MASTER.001 | depends_on | KB existence and navigation | 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
XREF: UE.KB.GOV.RULES.011 | governs | KB boundaries and no-dup | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

## 0) PURPOSE
Этот realm хранит **методики маркетинга и дистрибуции**:
- позиционирование и сообщения
- аудитория и сегменты
- каналы и формат контента
- релиз-план
- воронка контента
- метрики и обратная связь

Realm не хранит рекламные креативы/ролики/баннеры как файлы — только знание и правила.

---

## 1) POSITIONING (CORE)
- unique promise (что мы обещаем)
- differentiation (почему мы другие)
- proof points (что подтверждает)
- tone & voice (как звучим)

---

## 2) AUDIENCE MODELS
- segments
- intents (зачем смотрят)
- barriers (почему не смотрят)
- hooks (что цепляет)

---

## 3) MESSAGING SYSTEM
- message hierarchy (top → sub)
- taglines / one-liners
- forbidden claims (чего не обещаем)

---

## 4) CHANNEL STRATEGY
- channels list (platforms)
- per-channel format rules
- cadence (частота)
- adaptation policy (как один материал перерабатывается под разные каналы)

---

## 5) CONTENT FUNNEL
- awareness
- interest
- conversion
- retention

Для каждого этапа:
- content types
- KPI
- “what success looks like”

---

## 6) RELEASE PLANNING
- release calendar concepts
- teaser → trailer → drop → follow-up
- launch checklist
- crisis plan (если фидбек негативный)

---

## 7) MEASUREMENT (METRICS)
- north star metric
- supporting metrics
- experiment rules (A/B если нужно)
- feedback loop into KB (что считаем знанием после релиза)

---

## 8) LINKING TO ENTITIES / SEASONS (UID-FIRST)
Если маркетинг привязан к:
- сезону/арке/проекту (если это сущность) → UID
- персонажу/фракции/локации → ENTITY_UID

Pattern:
XREF:
- XREF: <TARGET_UID> | references | "marketing usage" | <path(optional)>

---

## 9) EXAMPLES / PLAYBOOKS (OPTIONAL)
> Примеры конкретных стратегий, но с ссылками UID-first на сущности.

---

## 10) OPEN QUESTIONS / TODO (OPTIONAL)
- (list)

--- END.
