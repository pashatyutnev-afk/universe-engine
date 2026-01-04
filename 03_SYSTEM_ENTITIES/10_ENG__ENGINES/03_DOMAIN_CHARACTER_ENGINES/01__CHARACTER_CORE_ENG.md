# Character Core Engine
FILE: 01__CHARACTER_CORE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines canonical character identity core (role, need, wound, mask, contradiction)

---

## PURPOSE

Создаёт **ядро персонажа** — минимальный набор, который делает его:
- узнаваемым
- внутренне противоречивым (живым)
- пригодным для предсказания поведения
- готовым к росту

---

## INPUTS

- Role in story (функция)
- Starting context (мир/класс/работа/семья)
- Initial desire/goal seed (черновой)
- Initial wound/fear seed (черновой)

---

## OUTPUTS

- Character Core Card (каноническая карточка)
- Core contradictions list
- Non-negotiables (что он НЕ делает)
- Signature traits (2–3 отличительных)

---

## CANONICAL CHARACTER CORE CARD

- CHAR_ID
- ROLE: (protagonist / antagonist / mentor / etc.)
- PUBLIC MASK: каким он выглядит
- PRIVATE TRUTH: какой он внутри
- CORE NEED: что ему реально нужно (не “хочет”, а “нужно”)
- CORE WANT: что он хочет прямо сейчас
- WOUND: ключевая рана/страх
- LIE / FALSE BELIEF: во что он верит неправильно
- VALUE AXIS: главная ценностная ось (свобода/контроль/любовь/долг…)
- CONTRADICTION: 1–2 внутренних противоречия
- NON-NEGOTIABLES: табу / границы
- SIGNATURE: манера, привычка, “почерк”

---

## PROCEDURE

1) Define Role & Mask
2) Define Need vs Want
3) Define Wound + False belief
4) Define Value axis
5) Create contradiction:
   - желание A vs ценность B
   - страх vs амбиция
6) Set non-negotiables:
   - что он не пересекает даже под давлением
7) Output signature:
   - 2–3 штуки, которые делают его “не перепутаешь”

---

## VALIDATION RULES

- CC1: Need и Want не должны быть одинаковыми.
- CC2: У персонажа обязано быть хотя бы одно противоречие.
- CC3: Wound должен влиять на решения, иначе это декорация.
- CC4: Non-negotiables должны конфликтовать с историей (иначе они не тестируются).

---

## FAILURE MODES

- “идеальный персонаж” без противоречий
- цель без внутренней цены
- “маска” совпадает с “правдой”
- рана не проявляется в сценах

---

## INTEGRATION

- With MOTIVATION_DESIRE_ENG: Want/Need → цели и драйвы
- With MORAL_VALUE_ENG: ценностные границы
- With PSYCHOLOGY_ENG: рана и защитные реакции

---
OWNER: Universe Engine
STATUS: FIXED
