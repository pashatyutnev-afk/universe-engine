# KB — GAP FILL PRIORITY POLICY (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/42__KB_GAP_FILL_PRIORITY_POLICY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: POLICY
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.POL.GAP_PRIORITY.042
OWNER: SYSTEM
ROLE: Defines a deterministic prioritization policy for filling KB competence gaps (missing skill tags, missing packs, missing topics) using P1/P2/P3 priority tiers based on impact, frequency, risk, and dependency position.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created deterministic gap-fill priority policy for KB growth planning."
- REASON: "KB is the quality backbone; gaps must be closed in the most impactful order instead of random creation."
- IMPACT: "Directed KB expansion; faster quality gains; fewer low-value modules."
- CHANGE_ID: UE.CHG.2026-01-14.KB.POL.042

---

## 0) PURPOSE (KB)
Define how to prioritize what KB modules to create/extend next:
- competence packs
- topics
- checklists
- dictionaries/maps

Goal:
- maximize quality improvement per effort
- reduce failure modes and drift

---

## 1) PRIORITY TIERS (ENUM)
P1 — Critical
- blocks a core workflow or causes frequent failures
- high impact on output quality or safety
- prerequisite for many other modules (high centrality)

P2 — Important
- improves quality noticeably
- used often but not blocking
- reduces rework significantly

P3 — Nice-to-have
- niche use cases
- polish improvements
- long-tail edge cases

---

## 2) SCORING FACTORS (DETERMINISTIC)
Score each gap on these factors (0..3 each):

F1 Impact on output quality (0..3)
- 3: huge quality jump, fixes major defect class
- 2: noticeable improvement
- 1: minor polish
- 0: negligible

F2 Frequency of use (0..3)
- 3: used in most runs
- 2: used weekly/daily in pipeline
- 1: occasional
- 0: rare

F3 Risk / Cost of failure (0..3)
- 3: produces broken canon, safety/legality risks, or severe regressions
- 2: frequent rework or audience rejection
- 1: mild annoyance
- 0: low consequence

F4 Dependency centrality (0..3)
- 3: prerequisite for many modules (governance/tooling)
- 2: prerequisite for several packs
- 1: local dependency
- 0: isolated

F5 Coverage hole severity (0..3)
- 3: missing critical skill tag cluster (no pack covers it)
- 2: partially covered (L1 only)
- 1: covered but weak (needs L2/L3)
- 0: already strong

Total score = F1+F2+F3+F4+F5 (0..15)

---

## 3) PRIORITY ASSIGNMENT RULE
- P1 if score ≥ 12 OR F3=3 OR F4=3
- P2 if score 7..11
- P3 if score ≤ 6

Override:
- Governance gaps default to at least P2.
- If a gap blocks ACTIVE promotion of a key module, treat as P1.

---

## 4) GAP TYPES & DEFAULT PRIORITIES
GAP_TYPE:
- GOVERNANCE_BASELINE (default P1/P2)
- CORE_DOMAIN_METHOD (default P1)
- QA_GATE_MISSING (default P1/P2 depending on risk)
- COMPETENCE_PACK_MISSING (default P1)
- SKILL_TAG_MISSING (taxonomy update) (default P2)
- EDGE_CASE_ENHANCEMENT (default P3)

---

## 5) ACTION RULES (WHAT TO DO)
For each prioritized gap:
- If missing entirely:
  - CREATE new atomic module/pack
- If partial:
  - EXTEND existing pack to L2/L3
- If conflicting:
  - DEPRECATE older and point to canon
- Always:
  - register in master index
  - update scorecard

---

## 6) OUTPUT TEMPLATE (PRIORITY LIST)
GAP_PRIORITY_LIST:
- GAP: <tag or module name>
  - PRIORITY: P1/P2/P3
  - SCORE: <0..15>
  - FACTORS: F1=.. F2=.. F3=.. F4=.. F5=..
  - ACTION: CREATE/EXTEND/DEPRECATE
  - TARGET: <pack uid or planned name>
  - WHY: <1 line>

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- gaps are created without priority assignment for P1/P2 items
- low-tier gaps (P3) consume effort while P1 exists
- scorecard is not updated after gap fill
- new module created without master-index registration

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.TPL.SKILL_TAG_SCORECARD.041 | WHY: scorecard identifies and quantifies gaps
- XREF: UE.KB.DICT.SKILL_TAGS.040 | WHY: canonical tag set for gap detection
- XREF: UE.KB.TOPIC.META.GAP_FILL.004 | WHY: create-module vs hard stop protocol
- XREF: UE.KB.STD.MASTER_INDEX_REG.008 | WHY: registration/existence rule

--- END.
