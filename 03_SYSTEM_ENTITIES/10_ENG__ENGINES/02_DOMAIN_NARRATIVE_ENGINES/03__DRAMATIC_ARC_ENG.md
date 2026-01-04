# Dramatic Arc Engine
FILE: 03__DRAMATIC_ARC_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
LEVEL: L2
STATUS: ACTIVE
VERSION: 1.0
ROLE: Designs and validates dramatic/emotional escalation arcs

---

## PURPOSE

Создаёт и контролирует **драматическую эскалацию**:
- рост/изменение напряжения
- эмоциональные пики/спады
- последовательность потерь/находок
- ощущение “движения к неизбежному”

---

## INPUTS

- Structure beats (из STORY_STRUCTURE_ENG)
- Character vulnerabilities / desires
- Stakes map (из TENSION_STAKES_ENG)
- Scene list draft

---

## OUTPUTS

- Arc Graph: (tension over time)
- Peak plan: где пики, где разрядка
- Required escalations: чего не хватает
- Anti-flatness flags: где провалы/плато

---

## ARC COMPONENTS

- Pressure: внешнее давление
- Cost: цена выбора
- Exposure: раскрытие уязвимости
- Irreversibility: необратимость шагов
- Consequence: последствия решений

---

## PROCEDURE

1) Define Starting Baseline
2) Place Peaks:
   - минимум 2–3 пика на крупную историю
3) Place Valleys:
   - разрядки должны:
     - (a) давать смысл (рефлексия/план)
     - (b) готовить следующий рывок
4) Escalation Ladder:
   - каждое повышение либо увеличивает:
     - ставки
     - риск
     - цену
     - разоблачение
5) Irreversibility Check:
   - к midpoint и к финалу должны быть необратимые шаги

---

## VALIDATION RULES

- D1: Драма не растёт линейно — но обязана меняться (пики/плато/повороты).
- D2: Каждая разрядка должна иметь функцию, иначе это “пустая сцена”.
- D3: Эскалация не может быть только “громче” — должна быть “глубже”.
- D4: Финальный пик должен быть подготовлен на уровне цены и уязвимости.

---

## FAILURE MODES

- Плоская середина (ничего не меняется)
- Пики без последствий
- Слишком много пиков без дыхания (усталость)
- Разрядки без смысла (пустота)

---

## INTEGRATION

- With PACING_RHYTHM_ENG: ритм дыхания истории
- With SCENE_CONSTRUCTION_ENG: сцены обязаны менять давление
- With CHARACTER_EVOLUTION_ENG: драматическая дуга связана с внутренней

---
OWNER: Universe Engine
STATUS: FIXED
