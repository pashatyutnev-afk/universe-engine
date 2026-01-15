# SPC PRO PACK — TOOL (T05) — CONSONANT_ATTACK_PROTECTOR (TARGET→DIRECTIVES) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/07__TOOLS/05__T05__CONSONANT_ATTACK_PROTECTOR.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: TOOL
TOOL_ID: T05
TOOL_NAME: CONSONANT_ATTACK_PROTECTOR
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.TOOL.VOCAL_DIRECTOR.T05.CONSONANT_ATTACK_PROTECTOR.001
OWNER: SYSTEM
ROLE: Generates performer-actionable attack protection notes for P0 targets: target→(<=3 directives)→pass_test. Prevents consonant loss without resorting to mixing advice or lyric rewrites.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Tool T05 CONSONANT_ATTACK_PROTECTOR for VOCAL_DIRECTOR."
- REASON: "Most intelligibility failures are caused by swallowed consonant attacks under lift."
- IMPACT: "Clear, repeatable performer directives for P0 recognition."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.TOOL.VD.T05.001

---

## 0) PURPOSE
Produce stable clarity action notes:
- ATTACK_PROTECTION_NOTES

Supports Gate:
- G3 INTELLIGIBILITY (Gate D + HF-3)

---

## 1) INPUTS (REQUIRED)
- MUST_HEAR_WORDS.P0 (from T02)
Optional:
- MUST_HEAR_PHRASES (from T03) for context
- language label (RU/EN/etc.)
- style notes (rap/sing/mixed)

Rules:
- Targets must come from MUST_HEAR_WORDS.P0 only.
- Tool does not invent new targets.

---

## 2) OUTPUT BLOCK (STABLE NAME)
T05 MUST output:

### ATTACK_PROTECTION_NOTES
For each target (P0 word), include:
- target: "<P0 word>"
  - directives:
    - D1:
    - D2: (optional)
    - D3: (optional)
  - do_not_do (optional):
    - "<common failure pattern>"
  - pass_test:
    - "<test statement>"

---

## 3) DIRECTIVE RULES (STRICT)
- directives per target: 1..3 (hard max = 3)
- directives must be performer-actionable (delivery/mouth/attack)
- no audio engineering instructions (no EQ/compression)
- no lyric changes

Allowed directive types (examples):
- Onset clarity: “hit initial consonant cleanly before vowel”
- Tail clarity: “finish final consonant; do not drop the tail”
- Attack window: “reduce grit only on the first 80–150ms of the word”
- Space: “micro-gap before target word (performance timing)”
- Stress focus: “emphasize consonant cluster; keep vowel shorter”

Forbidden directive types:
- plugin chain or mix settings
- rewriting word/phrase
- arrangement ownership claims

---

## 4) PASS_TEST RULE (MANDATORY)
Each target must have a pass_test:
- phrased as a listener test:
  - “On first listen, the word '<target>' is recognized in the hook.”

If the target appears in a phrase:
- include phrase boundary reminder (copy-exact if available).

---

## 5) PROCEDURE (DETERMINISTIC STEPS)
Step 1 — Validate inputs
- If MUST_HEAR_WORDS.P0 missing → GAP/STOP.

Step 2 — For each P0 word, choose 1–3 directives
- Pick minimal set that addresses:
  - onset clarity
  - tail clarity (if relevant)
  - texture window control (if aggressive style)

Step 3 — Add “do_not_do” for common failure
- optional, 1 line

Step 4 — Add pass_test
- required, 1 line

Step 5 — Emit ATTACK_PROTECTION_NOTES
- stable structure per target

---

## 6) STOP / GAP CONDITIONS
Stop and request missing inputs if:
- P0 list missing
- language missing (do not infer; affects consonant guidance nuance)

---

## 7) ANTI-SCOPE / ANTI-GUESSING
Forbidden:
- claiming success without testing
- inventing targets not in P0
- mixing chain advice
- lyric rewrites

---

## 8) TRACE
TRACE:
- TOOL: T05
- OUTPUT: ATTACK_PROTECTION_NOTES
- SUPPORTS_GATE: G3

--- END.
