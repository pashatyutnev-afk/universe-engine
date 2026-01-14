# PLAYBOOK — VOCAL DIVERSITY BOOST (ANTI “SAME SINGER”) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/03__METHOD_PLAYBOOKS/05__PLAYBOOK__VOCAL_DIVERSITY_BOOST.md

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
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.VOCAL_DIVERSITY.001
OWNER: SYSTEM
ROLE: Deterministic method to increase vocal differentiation in music generator outputs: role ownership per section, contrast levers, delivery constraints, targeted negatives, and recheck. Designed to fix “same singer syndrome” without rewriting the whole prompt.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created vocal diversity boost playbook: diagnostics, contrast levers, role maps, negative specs, and minimal-delta patch strategy."
- REASON: "Vocal sameness is a top failure mode; needs a repeatable fix method."
- IMPACT: "More distinct vocal parts and less repetition of voice fingerprint."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.PACK.PROMPT.PB.VOCAL.001

---

## 0) INPUTS (REQUIRED)
- BASELINE_PROMPT_CONTRACT (frozen)
- SYMPTOMS (observed):
  - same timbre across sections
  - rap vs melodic not distinct
  - call/response absent
- TARGET VOCAL SETUP:
  - 1 voice (must still vary delivery)
  - 2 roles (A/B)
  - 3 roles (A/B/stacked chorus) (advanced)
- RECHECK PLAN (optional gates UIDs)

---

## 1) OUTPUTS
- VOCAL_ROLE_MAP (per section)
- VOCAL_CONTRAST_BLOCK (insert/update in prompt)
- TARGETED_NEGATIVE_SPECS (voice-related)
- PATCH_PROMPT (minimal delta)
- RECHECK_MINI

---

## 2) DIAGNOSTIC SIGNALS (WHEN TO USE)
Use this playbook if:
- chorus feels like same vocalist as verse
- rap verses and melodic chorus share same delivery
- voice “color” and range do not shift between sections
- multiple tracks in catalog sound like same singer

Do NOT use if:
- issue is structure/hook (use hook playbook)
- issue is lyric repetition (use anti-repetition playbook)

---

## 3) VOCAL DIFFERENTIATION LEVERS (CANON)
Pick 2–4 levers; do not overload.

LEVER L1 — ROLE OWNERSHIP (strongest)
- Assign who leads each section:
  - Verse = Voice A (rap)
  - Chorus = Voice B (melodic)
  - Bridge = A/B or new delivery mode

LEVER L2 — DELIVERY MODE CONTRAST
- Specify delivery behaviors:
  - A: percussive, tight rhythm, clipped phrases
  - B: sustained notes, open vowels, wider phrasing
(Use observable language, not abstract “cool voice”.)

LEVER L3 — RANGE SEPARATION (principle)
- A sits lower/mid; B sits higher/mid.
(No exact notes; principle only.)

LEVER L4 — TIMBRE CONTRAST (principle)
- A darker/rougher; B brighter/cleaner (or vice versa).
(Principles; avoid concrete “voice model” claims.)

LEVER L5 — CALL/RESPONSE or ADLIB LAYER
- Chorus: add call/response or adlibs layer as a role, not as heavy arrangement list.

LEVER L6 — SECTION-SPECIFIC PROCESSING INTENT (light)
- A more dry/intimate; B bigger/chorusy (principle-level only).

Rule:
- Always include L1 + one of (L2/L3/L4) for best effect.

---

## 4) BUILD VOCAL ROLE MAP (PER SECTION)
VOCAL_ROLE_MAP (COPY):
- Intro:
- Verse 1:
- Chorus:
- Verse 2:
- Bridge:
- Final Chorus:
- Outro:

Example (2 roles):
- Verse 1: Voice A (rap delivery, percussive)
- Chorus: Voice B (melodic, sustained)
- Bridge: Voice A/B call-response (short)
- Final chorus: B lead + A adlibs (optional)

---

## 5) WRITE VOCAL_CONTRAST_BLOCK (INSERT/UPDATE)
VOCAL_CONTRAST_BLOCK (COPY):
- VOCALS:
  - ROLE MAP: <short>
  - VOICE A: <delivery behaviors + range/timbre principles>
  - VOICE B: <delivery behaviors + range/timbre principles>
  - CONTRAST RULE: “A and B must sound clearly different across sections”
  - OPTIONAL: call/response in chorus

Keep this block compact (≤ 8–12 lines).

---

## 6) TARGETED NEGATIVE SPECS (VOICE)
Choose 3–6, only voice-related:

NEGATIVE_VOICE:
- avoid identical vocal timbre across sections
- avoid same delivery mode for verse and chorus
- avoid monotone singing across whole song
- avoid chorus sounding like verse
- avoid uniform pitch range across sections

Do not add unrelated negatives here.

---

## 7) PATCH STRATEGY (MINIMAL DELTA)
Delta rule:
- only modify VOCAL_INTENT_BLOCK + add 1–2 negatives.

Patch prompt (COPY):
PATCH_PROMPT:
- Keep everything else unchanged.
- Replace/update VOCAL_INTENT_BLOCK with VOCAL_CONTRAST_BLOCK.
- Add NEGATIVE_VOICE items (3–6).
- Do not change STYLE_BLOCK or STRUCTURE_BLOCK.

If still same after 2 attempts:
- escalate:
  - strengthen role ownership (L1)
  - add call/response (L5)
  - increase contrast specificity (L2)

---

## 8) RECHECK MINI (POST-GEN)
RECHECK_MINI:
- [ ] Verse voice differs from chorus voice (obvious)
- [ ] Rap delivery is distinct from melodic delivery (if applicable)
- [ ] Chorus lead feels like a different persona/texture
- [ ] If call/response used: audible contrast exists
- [ ] No new major artifacts introduced

Result: PASS/REWORK/FAIL

---

## 9) TRACE (MINIMUM)
TRACE_NOTES:
- BASELINE_ID:
- LEVERS_USED: [L1, L2, ...]
- NEGATIVES_ADDED_COUNT:
- RESULT:
- LOOP_COUNT:
- MEMORY_REUSE: YES/NO
- WEB_LOOKUP_USED: YES/NO

---

## 10) RELATED (UID-ONLY)
XREF:
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.PATCH_MIN.001 | WHY: minimal delta discipline
- UE.KB.SPC.PACK.PROMPT_ARCHITECT.PB.DIAG_REWORK.001 | WHY: if multiple failures coexist
- UE.KB.SOUND.TOPIC.VOCAL_DIVERSITY_INTENT.001 (PLACEHOLDER) | WHY: deeper topic module when created
- UE.KB.QA.STD.CONNECTOR.001 | WHY: recheck discipline

--- END.
