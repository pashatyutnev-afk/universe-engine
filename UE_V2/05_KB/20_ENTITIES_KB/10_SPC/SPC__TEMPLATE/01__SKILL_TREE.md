# 01__SKILL_TREE — SPC PRO PACK (TEMPLATE)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/SPC__TEMPLATE/01__SKILL_TREE.md
SCOPE: Knowledge Base — Entities KB — SPC — Pro Pack Template
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: SPC_PRO_PACK (skill tree + responsibilities + failure modes)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.SPC.PRO_PACK.SKILL_TREE.001
OWNER: SYSTEM
ROLE: Canonical skill tree template for any SPC Pro Pack (responsibilities → skills → observable outcomes)

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Initial template for SPC Pro Pack skill tree."
- REASON: "Make scope executable: outputs mapped to skills and observable outcomes."
- IMPACT: "All SPC packs must include a skill tree in this structure."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.TPL.SKILLTREE.001

---

## PURPOSE (LAW)
Этот документ фиксирует **дерево навыков SPC** как операциональную структуру:
- обязанности → навыки → наблюдаемые outcomes → типовые провалы → “как чинить”.

---

## BINDINGS (MUST MATCH PASSPORT)
- PACK_UID: <PACK_UID>
- SPC_ENTITY_UID: <SPC_ENTITY_UID>
- TARGET_PROFICIENCY_LEVEL: <L1|L2|L3|L4>
- PRIMARY_OUTPUTS (from passport):
  - <output_1>
  - <output_2>

---

## RESPONSIBILITIES (WHAT SPC OWNS)
> Что SPC обязуется делать. Формулируй как “produce/ensure”.

- R1: <responsibility_1>
- R2: <responsibility_2>
- R3: <responsibility_3>

---

## FORBIDDEN ACTIONS (ABSOLUTE)
> Запреты поведения/решений внутри компетенции. Дублировать с паспортом можно, но тут — в форме действий.

- F1: <forbidden_action_1>
- F2: <forbidden_action_2>

---

## SKILL TREE (TREE → LEAF → OUTCOME)
> Формат: DOMAIN → SKILL → SUBSKILL → OUTCOME (observable) → EVIDENCE.

### DOMAIN A — <domain_name>
#### A1 — <skill_name>
- SUBSKILLS:
  - A1.1 <subskill_name>
  - A1.2 <subskill_name>
- OUTCOMES (OBSERVABLE):
  - O-A1-1: <what must be true in output>  
    - EVIDENCE: <what proves it>
    - VALIDATED_BY (UID-ONLY): <GATE_UID or CHK_UID>
  - O-A1-2: <...>

#### A2 — <skill_name>
- SUBSKILLS:
  - A2.1 <...>
- OUTCOMES:
  - O-A2-1: <...>

### DOMAIN B — <domain_name>
#### B1 — <skill_name>
- SUBSKILLS:
  - B1.1 <...>
- OUTCOMES:
  - O-B1-1: <...>

---

## OUTPUT → SKILL TRACE (MANDATORY)
> Каждому PRIMARY_OUTPUT должен соответствовать минимум один outcome и один gate/check.

- <output_1>:
  - SUPPORTING_OUTCOMES: O-A1-1, O-A2-1
  - MIN_VALIDATION: <GATE_UID_1>, <CHK_UID_1>
- <output_2>:
  - SUPPORTING_OUTCOMES: O-B1-1
  - MIN_VALIDATION: <GATE_UID_2>

---

## COMMON FAILURES (FAIL MODES)
> Типовые провалы. Каждый должен ссылаться на skill/outcome.

### FM-001 — <failure_name>
- RELATED_SKILL/OUTCOME: <A1 / O-A1-1>
- SYMPTOMS:
  - <symptom_1>
- LIKELY_CAUSES:
  - <cause_1>
- QUICK FIX (ONE AXIS):
  - <minimal change action>
- VALIDATE_AFTER:
  - <GATE_UID or CHK_UID>

### FM-002 — <failure_name>
- RELATED_SKILL/OUTCOME: <...>

---

## ESCALATION (WHEN TO STOP)
> Когда SPC обязан остановиться и эскалировать.

- If missing required inputs from passport → STOP + request inputs.
- If scope boundary violated (EXCLUDES) → STOP + route to correct entity/pack.
- If gates repeatedly fail after one-axis fixes → STOP + request higher-level decision.

---

## TOPIC SUPPORT (UID-ONLY)
> Тут только UID-список топиков, которые этот SPC использует как базу знаний.

- TOPIC_UIDS:
  - <TOPIC_UID_1> — <why>
  - <TOPIC_UID_2> — <why>

---
END
