# CHARACTER CRAFT (KB REALM) (CANON)
FILE: 04_KNOWLEDGE_BASE/02_CHARACTER_CRAFT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: REALM
REALM: CHARACTER_CRAFT
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.REALM.CHARACTER.102
OWNER: SYSTEM
ROLE: Knowledge realm for character craft: identity, motivation, arcs, behaviors, voice, relationships, and character consistency. Provides methods and rules; does not replace KB entity passports.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MAJOR
- SUMMARY: "Нормализован realm Character: Doc Control header + каркас разделов + правила связи с паспортами (registry-first, UID-first)"
- REASON: "Realm должен быть методологией и не превращаться в паспорта"
- IMPACT: "All character knowledge placement"

---

## XREF (UID-first)
XREF: UE.KB.IDX.MASTER.001 | depends_on | KB existence and navigation | 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
XREF: UE.KB.GOV.RULES.011 | governs | entity vs knowledge rules | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md
XREF: UE.KB.TPL.ENTITY_PASSPORT.015 | references | how character entities are recorded | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md
XREF: UE.KB.GOV.REGISTRY.012 | references | entity existence via registry | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md
XREF: UE.STD.SPEC.NAT_GATES.106 | references | character naturalness checks | 02_STANDARDS/01_SPECIFICATIONS/06__NATURALNESS_GATES_STANDARD.md

---

## 0) PURPOSE
Этот realm хранит **методики и правила создания персонажей**:
- идентичность и ядро персонажа
- мотивации и внутренние конфликты
- арки и изменения
- поведение и выбор
- голос (voice) и речевые паттерны
- отношения и социальная динамика
- consistency и naturalness

Realm НЕ является паспортом персонажа.
Персонажи как сущности живут в:
- `04_KNOWLEDGE_BASE/10_ENTITIES/CHARACTER/*`
и существуют только если зарегистрированы в KB Global Registry.

---

## 1) CHARACTER AS A SYSTEM (CORE MODEL)
### 1.1 Identity ядро
- Кто он (самоопределение)
- Чего он хочет (want)
- В чём нуждается (need)
- Чего боится/избегает (avoid)

### 1.2 Contradiction (обязательная “трещина”)
- Внутреннее противоречие = источник движения
- Поведение должно быть объяснимым, но не линейным

---

## 2) MOTIVATION & DRIVE
- primary drive
- secondary drives
- cost of desire
- values hierarchy (что не продаст)

---

## 3) ARC DESIGN
### 3.1 Arc types
- growth arc
- fall arc
- flat arc
- revelation arc

### 3.2 Arc checkpoints
- baseline state
- rupture (inciting)
- escalation
- choice under pressure
- new equilibrium

---

## 4) BEHAVIOR & DECISIONS (SHOW, DON’T TELL)
- decision rules
- stress behaviors
- coping mechanisms
- micro-habits that reveal core

---

## 5) VOICE (DIALOGUE + INTERNAL LOGIC)
- diction level
- rhythm/tempo
- taboo words / preferred words
- default emotional mask
- truth vs performance (что говорит vs что делает)

---

## 6) RELATIONSHIPS (NETWORK)
- attachment types
- power dynamics
- trust economy
- conflict vectors

Если отношения важны как объект:
- можно заводить отдельную сущность типа RELATIONSHIP (если реально нужно),
иначе — XREF между паспортами персонажей.

---

## 7) CONSISTENCY RULES (CHARACTER CONTINUITY)
Checklist:
- мотивация → действие согласованы
- изменения арки объяснимы “цепью событий”
- персонаж не обладает знаниями “из воздуха”
- эмоциональные реакции соответствуют истории

---

## 8) NATURALNESS (QUALITY GATES)
Рекомендуется при написании:
- применять NAT gates и фиксировать “провалы” как правки, а не как “особенность”

Если делаешь оценку:
- использовать формат `NAT_EVALUATION` (см. NAT marking module)

---

## 9) LINKING TO CHARACTER ENTITIES (UID-FIRST)
Если правило/пример про конкретного персонажа:
- ссылка только через ENTITY_UID (или через паспортный путь как доп.)

Pattern:
XREF:
- XREF: <CHAR_ENTITY_UID> | references | "example usage" | <passport-path(optional)>

---

## 10) EXAMPLES (OPTIONAL)
> Примеры методов на конкретных персонажах.
> Внутренние ссылки — UID-first.

---

## 11) OPEN QUESTIONS / TODO (OPTIONAL)
- (list)

--- END.
