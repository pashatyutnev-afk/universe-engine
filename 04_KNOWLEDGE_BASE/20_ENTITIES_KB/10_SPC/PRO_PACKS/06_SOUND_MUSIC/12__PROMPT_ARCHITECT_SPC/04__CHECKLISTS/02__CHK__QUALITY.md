# CHECKLIST — QUALITY (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/04__CHECKLISTS/02__CHK__QUALITY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: CHECKLIST
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.CHK.PROMPT_ARCHITECT.QUALITY.001
OWNER: SYSTEM
ROLE: Fast quality sanity checklist for PROMPT_ARCHITECT prompt contracts before generation/finalization. Produces PASS/REWORK/FAIL and points to the relevant gates/playbooks for fixes.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created quality checklist for PROMPT_ARCHITECT: contract sanity, hook/structure, vocal intent, repetition control, style stability, and overload checks."
- REASON: "Cheap preflight check catches most avoidable failures before running generators."
- IMPACT: "Higher pass rate and fewer wasted iterations."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.CHK.QUALITY.001

---

## 0) CONTRACT SANITY
- [ ] STYLE_BLOCK exists and is not contradictory
- [ ] STRUCTURE_BLOCK exists and has verse/chorus clarity (if full song)
- [ ] VOCAL_INTENT_BLOCK exists (if vocals are in scope)
- [ ] NEGATIVE_SPEC_BLOCK exists and is targeted (not spam)
- [ ] CONSTRAINTS_BLOCK includes format + duration/length intent

If any core block missing → REWORK.

---

## 1) HOOK & STRUCTURE
- [ ] Chorus/hook is explicitly labeled
- [ ] Hook intent is clear (early/strong if required)
- [ ] Verse and chorus roles are not blurred

If blurred → REWORK.

---

## 2) VOCAL INTENT (IF RELEVANT)
- [ ] Role ownership per section is explicit (A verses / B chorus) OR delivery contrast for single voice
- [ ] 2–4 contrast levers exist (delivery + range/timbre principles)
- [ ] At least 1 targeted voice negative exists (recommended)

If vibes-only vocal plan → REWORK.

---

## 3) REPETITION CONTROL
- [ ] Repetition policy is stated (what may repeat and where)
- [ ] Verse novelty constraint exists (if verses exist)
- [ ] At least 1 targeted repetition negative exists (recommended)

If repetition forbidden everywhere but hook needed → REWORK (contradiction).

---

## 4) STYLE FINGERPRINT STABILITY
- [ ] Primary style identity exists
- [ ] Anchors are 3–6 (roles, not inventories)
- [ ] If fusion used, dominance rule exists
- [ ] No genre soup (too many genres)

If anchors too many or too few → REWORK.

---

## 5) CONTROL DENSITY (OVERLOAD CHECK)
Heuristics:
- [ ] Positive specs are not excessively long (≈ ≤ 14 lines)
- [ ] Negatives not excessively long (≈ ≤ 14 items)
- [ ] No long inventories of instruments/genres

If overloaded → REWORK (prune).

---

## 6) RESULT RULE
PASS:
- all sections 0–5 are OK
- no obvious contradictions
- overload not detected

REWORK:
- 1–3 localized issues exist that can be fixed via minimal patch

FAIL:
- multiple core blocks missing
- heavy contradictions or severe overload
- structure unclear and requires rebuild

---

## 7) NEXT ACTIONS (IF REWORK/FAIL)
If contract sanity fails:
- run Gate 01 (Prompt Contract Clarity) + PB-01 CORE WORKFLOW

If vocal intent weak:
- run Gate 02 + PB-05 VOCAL DIVERSITY BOOST

If repetition weak:
- run Gate 03 + PB-06 ANTI-REPETITION FIX

If style drift/clutter:
- run Gate 04 + PB-07 STYLE STABILIZER

If iteration discipline issue:
- run Gate 05 + PB-02 ONE-AXIS VARIANTS

---

## 8) RELATED (UID-ONLY)
GATE LINKS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001
- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001
- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001
- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001

--- END.
