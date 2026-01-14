# PLAYBOOK — STYLE FINGERPRINT STABILIZER (DRIFT CONTROL) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/03__METHOD_PLAYBOOKS/07__PLAYBOOK__STYLE_FINGERPRINT_STABILIZER.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: PLAYBOOK
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.STYLE_STABILIZE.001
OWNER: SYSTEM
ROLE: Deterministic method to stabilize genre/style fingerprint: select anchor markers, apply dominance rules for fusion, reduce clutter/contradictions, and patch prompts minimally to stop drift while preserving identity.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created style fingerprint stabilizer playbook: drift diagnostics, anchor markers, dominance rules, de-clutter steps, and recheck."
- REASON: "Style drift causes catalog inconsistency and random outputs; needs a repeatable correction method."
- IMPACT: "More coherent genre identity and fewer chaotic fusions."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.PACK.PROMPT.PB.STYLE.001

---

## 0) INPUTS (REQUIRED)
- BASELINE_PROMPT_CONTRACT (frozen)
- DRIFT_SYMPTOMS (observed):
  - output loses genre identity
  - random blending of conflicting genres
  - instrumentation role confusion
  - “too many ideas” feeling
- TARGET_STYLE_IDENTITY:
  - PRIMARY genre (must dominate)
  - SECONDARY touch (optional)
- RECHECK (optional gate UIDs)

---

## 1) OUTPUTS
- STYLE_FINGERPRINT_ANCHORS (3–6 markers)
- DOMINANCE_RULE (primary + touch)
- DE-CLUTTER_PATCH (minimal delta)
- RECHECK_MINI

---

## 2) DRIFT DIAGNOSTICS (WHEN TO USE)
Use this playbook if:
- chorus/verse feel like different genres unintentionally
- track sounds like “random playlist blend”
- prompt lists many genres or conflicting descriptors
- output changes identity across generations unpredictably

Do NOT use if:
- the issue is hook timing or vocals; use the dedicated playbooks first.

---

## 3) ANCHOR MARKERS (CANON)
Choose 3–6 anchors total. Prefer “roles” over “inventories”.

Anchor categories:
- A1 RHYTHM FEEL (one):
  - half-time stomp / driving rock pulse / syncopated industrial groove

- A2 DRUM TONE ROLE (one):
  - punchy acoustic kit / hybrid electronic hits / gated industrial hits

- A3 GUITAR ROLE (one):
  - chug riffs / tight palm-mute rhythm / sparse accent riffs

- A4 SYNTH ROLE (one):
  - glitch lead accents / atmospheric pads / industrial stabs (pick one primary role)

- A5 VOCAL AESTHETIC (one):
  - rap verses + melodic chorus / chant chorus (choose a single main plan)

- A6 MIX INTENT (optional):
  - clean aggressive / gritty raw (choose one direction)

Rule:
- If you pick A4 glitchy synth leads, do not also add multiple other “lead” roles; keep one lead.

---

## 4) DOMINANCE RULE (FUSION CONTROL)
If mixing genres:
- Primary genre must dominate (70–90% intent)
- Secondary is a “touch” (10–30%)
- Explicitly state what must stay primary:
  - rhythm feel OR guitar role OR chorus structure (choose 1–2)

DOMINANCE_BLOCK (COPY):
- PRIMARY: <genre> (dominant)
- SECONDARY: <touch> (subtle)
- MUST STAY PRIMARY:
  - <anchor 1>
  - <anchor 2>

---

## 5) DE-CLUTTER RULES (REMOVE CONTRADICTIONS)
Remove:
- multiple genre stacks (“nu metal + trap + dnb + reggae + …”)
- conflicting mix adjectives (clean + lo-fi muddy)
- too many instrument lists
- multiple lead roles

Compression rule:
- keep 3–6 anchors
- keep one dominant texture direction
- keep one rhythm feel

---

## 6) PATCH STRATEGY (MINIMAL DELTA)
Delta rule:
- modify only STYLE_BLOCK (and possibly one negative line).
- keep structure/vocals unchanged unless drift is caused by vocal plan conflicts.

Patch prompt (COPY):
PATCH_PROMPT:
- Keep everything else unchanged.
- Replace STYLE_BLOCK with:
  - 3–6 anchors
  - dominance rule (primary + touch)
  - remove contradictions
- Add optional negative:
  - "avoid genre drift; keep primary style consistent"

Loop limit:
- 2 attempts before escalating to DIAGNOSE & REWORK.

---

## 7) RECHECK MINI (POST-GEN)
RECHECK_MINI:
- [ ] Primary genre identity is recognizable
- [ ] Secondary touch does not take over
- [ ] Verse and chorus share the same style world (no accidental genre split)
- [ ] No obvious contradictory texture cues
- [ ] Hook still works (if required)

Result: PASS/REWORK/FAIL

---

## 8) TRACE (MINIMUM)
TRACE_NOTES:
- BASELINE_ID:
- ANCHORS_SELECTED:
- DOMINANCE_RULE_USED: YES/NO
- CLUTTER_REMOVED (short):
- RESULT:
- LOOP_COUNT:
- MEMORY_REUSE: YES/NO
- WEB_LOOKUP_USED: YES/NO

---

## 9) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.PATCH_MIN.001 | WHY: minimal delta discipline
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.DIAG_REWORK.001 | WHY: escalation path
- UE.KB.SOUND.TOPIC.STYLE_FINGERPRINT_CONTROL.001 (PLACEHOLDER) | WHY: deeper topic module when created
- UE.KB.REF.GLOSSARY.GENRE_MARKERS.001 (PLACEHOLDER) | WHY: controlled vocabulary for anchors (future)

--- END.
