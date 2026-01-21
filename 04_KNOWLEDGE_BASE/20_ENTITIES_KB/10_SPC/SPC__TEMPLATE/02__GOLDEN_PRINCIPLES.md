# 02__GOLDEN_PRINCIPLES — SPC PRO PACK (TEMPLATE)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/02__GOLDEN_PRINCIPLES.md
SCOPE: Knowledge Base — Entities KB — SPC — Pro Pack Template
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: SPC_PRO_PACK (golden principles + limits + anti-patterns)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.SPC.PRO_PACK.GOLDEN.001
OWNER: SYSTEM
ROLE: Canonical principles/limits template to keep SPC packs deterministic and within scope.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Initial golden principles template for SPC Pro Packs."
- REASON: "Prevent scope creep and inconsistent decisions."
- IMPACT: "All SPC packs must declare principles, limits, and anti-patterns."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.TPL.GOLDEN.001

---

## PURPOSE (LAW)
Этот документ задаёт “внутренний компас” SPC:
- **что оптимизируем** (principles),
- **какие ограничения нельзя нарушать** (constraints),
- **какие ошибки повторяются** (anti-patterns),
- **где границы ответственности** (scope boundaries).

---

## BINDINGS (MUST MATCH PASSPORT)
- PACK_UID: <PACK_UID>
- SPC_ENTITY_UID: <SPC_ENTITY_UID>
- TARGET_PROFICIENCY_LEVEL: <L1|L2|L3|L4>

---

## GOLDEN PRINCIPLES (WHAT WE OPTIMIZE)
> 7–12 пунктов. Каждый пункт: правило → зачем → как проверить (gates/checks).

### P1 — <principle_name>
- RULE: <short rule statement>
- WHY: <reason>
- HOW TO CHECK:
  - VALIDATED_BY (UID-ONLY): <GATE_UID / CHK_UID>
  - OBSERVABLE SIGNAL: <what is visible in output>

### P2 — <principle_name>
- RULE: <...>
- WHY: <...>
- HOW TO CHECK: <...>

(…repeat…)

---

## CONSTRAINTS (HARD LIMITS INSIDE THE WORK)
> Это ограничения уровня “нельзя делать так”, даже если кажется быстрее.

### C1 — <constraint_name>
- LIMIT: <what is forbidden/limited>
- RISK IF VIOLATED: <what breaks>
- SAFE ALTERNATIVE: <preferred approach>
- VALIDATE:
  - <GATE_UID / CHK_UID>

### C2 — <...>

---

## SCOPE BOUNDARIES (COVERS / EXCLUDES)
> Дублирует паспорт, но в форме принципа “где остановиться”.

- COVERS (IN-SCOPE):
  - <covers_1>
- EXCLUDES (OUT-OF-SCOPE):
  - <excludes_1>
- STOP RULE:
  - If request falls into EXCLUDES → STOP + route to correct pack/entity.

---

## ANTI-PATTERNS (COMMON BAD MOVES)
> 8–15 пунктов. Каждый: симптом → почему плохо → чем заменить → чем проверить.

### AP-001 — <anti_pattern_name>
- SYMPTOM: <what it looks like>
- WHY IT FAILS: <cause/effect>
- REPLACEMENT PATTERN: <better approach>
- VALIDATE_AFTER:
  - <GATE_UID / CHK_UID>
- RELATED SKILL/OUTCOME:
  - <A1 / O-A1-1>

### AP-002 — <...>

---

## DECISION PRINCIPLES (WHEN MULTIPLE OPTIONS)
> Как принимать решения, когда есть несколько “норм” вариантов.

- D1: Prefer option with highest repeatability (least hidden assumptions).
- D2: Prefer minimal-change (one-axis) over multi-axis rework.
- D3: Prefer explicit tradeoffs and declare them (in notes) rather than implicit changes.

---

## SAFETY & ETHICS BOUNDARY (PACK INTERNAL)
> Без морализаторства — только границы допустимого.

- S1: <safety boundary>
- S2: <...>
- ESCALATE WHEN:
  - <condition_1>
  - <condition_2>

---

## “ONE AXIS” CHANGE DISCIPLINE (OPTIONAL BUT RECOMMENDED)
- RULE: Change only one axis per iteration.
- AXES LIST (examples):
  - style, structure, clarity, density, compliance, voice, pacing, etc.
- TRACKING:
  - Record axis changed in CHANGE_NOTE when updating pack.

---
END
