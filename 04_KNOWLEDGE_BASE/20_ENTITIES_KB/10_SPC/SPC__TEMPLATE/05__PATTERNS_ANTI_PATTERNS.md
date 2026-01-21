# 05__PATTERNS_ANTI_PATTERNS — SPC PRO PACK (TEMPLATE)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/05__PATTERNS_ANTI_PATTERNS.md
SCOPE: Knowledge Base — Entities KB — SPC — Pro Pack Template
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: SPC_PRO_PACK (patterns + anti-patterns + fix recipes)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.SPC.PRO_PACK.PATTERNS.001
OWNER: SYSTEM
ROLE: Canonical patterns/anti-patterns template (signals → fix recipes → validation binding).

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Initial patterns/anti-patterns template for SPC Pro Packs."
- REASON: "Capture repeatable good moves and common failure signatures."
- IMPACT: "Allows fast diagnosis and one-axis repairs linked to validation."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.TPL.PATTERNS.001

---

## PURPOSE (LAW)
Этот документ — “быстрый слой опыта”:
- **PATTERNS**: повторяемые хорошие решения.
- **ANTI_PATTERNS**: повторяемые ошибки.
- **SIGNALS**: признаки, что проблема уже возникла.
- **FIX RECIPES**: короткие рецепты исправления (желательно one-axis).
- **VALIDATION LINKS**: чем проверить исправление (UID-only).

> RULE: Это не учебник. Только операционные формулы + привязка к validation.

---

## BINDINGS (MUST MATCH PASSPORT)
- PACK_UID: <PACK_UID>
- SPC_ENTITY_UID: <SPC_ENTITY_UID>
- TARGET_PROFICIENCY_LEVEL: <L1|L2|L3|L4>

---

## PATTERN CONTRACT (MUST USE THIS SHAPE)
### FIELDS
- PATTERN_ID
- NAME
- WHEN TO USE
- STEPS (minimal)
- EXPECTED OUTCOME
- RISKS
- VALIDATE_AFTER (UID-only)

---

## ANTI-PATTERN CONTRACT (MUST USE THIS SHAPE)
### FIELDS
- ANTI_PATTERN_ID
- NAME
- SIGNALS
- WHY BAD (cause/effect)
- REPLACEMENT PATTERN
- FIX RECIPE (one-axis)
- VALIDATE_AFTER (UID-only)

---

## PATTERNS (GOOD)
### PT-001 — <pattern_name>
- WHEN TO USE: <context/trigger>
- STEPS:
  1) <step>
  2) <step>
- EXPECTED OUTCOME: <observable result>
- RISKS: <what can go wrong if misapplied>
- VALIDATE_AFTER (UID-ONLY):
  - <CHK_UID / GATE_UID>
- RELATED OUTCOMES:
  - <O-A1-1>

### PT-002 — <pattern_name>
- WHEN TO USE: <...>
- STEPS: <...>
- VALIDATE_AFTER: <...>

(…add as needed…)

---

## ANTI-PATTERNS (BAD)
### AP-001 — <anti_pattern_name>
- SIGNALS:
  - <signal_1>
  - <signal_2>
- WHY BAD: <cause/effect>
- REPLACEMENT PATTERN: PT-<id>
- FIX RECIPE (ONE AXIS):
  - AXIS: <clarity|structure|density|consistency|compliance|etc>
  - ACTION: <minimal change>
- VALIDATE_AFTER (UID-ONLY):
  - <CHK_UID / GATE_UID>
- RELATED FAIL MODE:
  - <FM-001>

### AP-002 — <anti_pattern_name>
- SIGNALS: <...>
- FIX RECIPE: <...>

---

## SIGNALS INDEX (FAST SCAN)
> Однострочник: сигнал → вероятная причина → куда идти (playbook/check)

- <signal>: <cause> → PB-03 + CHK-02
- <signal>: <cause> → PB-02 + <GATE_UID>

---

## FIX RECIPES INDEX (FAST MENU)
> Меню фиксов по типу проблемы.

### CLARITY FIXES
- RX-C-01: <recipe> → VALIDATE: <CHK_UID / GATE_UID>

### CONSISTENCY FIXES
- RX-K-01: <recipe> → VALIDATE: <...>

### SCOPE / COMPLIANCE FIXES
- RX-S-01: <recipe> → VALIDATE: <...>

---

## BINDINGS TO CASE LIBRARY
> Привязка паттернов к кейсам (когда кейсы появятся).

- PT-001 → CASE__GOOD:<case_id>
- AP-001 → CASE__BAD:<case_id>

---
END
