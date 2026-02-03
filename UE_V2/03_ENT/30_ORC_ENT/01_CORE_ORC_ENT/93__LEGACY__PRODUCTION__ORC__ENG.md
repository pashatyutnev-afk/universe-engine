FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/93__LEGACY__PRODUCTION__ORC__ENG.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE (LEGACY_ADAPTER)
DOMAIN: COR_ORC_ENT
KEY: LEGACY.PRODUCTION_ORC_ENG
UID: UE.V2.ENT.ORC.LEGACY.PRODUCTION_ORC_ENG.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Legacy adapter orchestrator for production tasks (ENG flavor).
Brings legacy “production pipeline” behavior into UE_V2 while enforcing RAW-only nav, minimal load, step-run cadence, deterministic packaging, and governance boundaries.

---

## [M] PURPOSE
- Execute legacy production flows inside UE_V2 without bypassing NAV/REG/XREF/KB/PIPE/LOG laws.
- Translate UE_V2 ROUTE_TOKEN + TASK_TEXT into controlled production outputs (prompt packs, lyrics drafts, release blueprints).
- Enforce anti-noise and anti-drift so outputs stay consistent across many releases.
- Reduce recognizability risks (repetition, obvious sourcing, template fingerprints) through controlled variation rules.

---

## [M] WHEN TO USE
Use this module only when:
- ROUTE_TOKEN.PIPE_SELECTED explicitly targets legacy production adapter, OR
- CORE uses legacy fallback due to missing domain production pipe and fallback is permitted by REQUIRED_CHECKS.

Do NOT use when:
- There is an active UE_V2 domain pipe for production/music/video and it is selected.
- The run requires canonical registry/entity mutations (albums as entities, passports, indexes, KB writes).
- The request implies prohibited content (copyright copying, disallowed violence instructions, targeted harassment).

---

## [M] HARD_RULES
- Adapter only:
  - Never changes routing decisions. Runs only after COR pipeline dispatcher selects it.
- RAW-only:
  - Any reference must resolve via IDX->RAW. No PATH обходы.
- Keys-only contract:
  - Inputs/outputs reference KEYS and check-ids, not raw URLs inside content blocks.
- Minimal load:
  - Open only REQUIRED_IDX + 1–3 target files max.
- Step-run:
  - Output only the increment required for the current "го" step.
- No direct entity writes:
  - May produce drafts/specs but must not mutate canonical registries, passports, or indexes.
- Compliance first:
  - If constraints conflict with safety or compliance, downshift or STOP.
- Output determinism:
  - Stable section ordering, stable deliverable titles, stable metadata keys.

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN, ARTIFACT_TYPE, MODE, PIPE_SELECTED, REQUIRED_IDX, REQUIRED_CHECKS, EXEC_MODE
- TASK_TEXT (required)
- MODE_HINT (optional)
  - FAST|RELEASE_READY|MASTERPIECE
- CONSTRAINTS (optional)
  - platform (Suno/other), duration_target, language, style, references, vocal_count, structure
- RUN_STATE (required)
  - STEP, STATUS, OPENED_KEYS (optional)
- LEGACY_HINT (optional)
  - legacy_profile: PROD_DEFAULT|PROD_RELEASE|PROD_SCALE
  - length_policy: FIXED|TARGETED (bounded)
  - variation_budget: LOW|MED|HIGH (bounded)

---

## [M] OUTPUTS
- LEGACY_EXEC_PLAN (internal)
  - mapping UE_V2 steps to legacy production actions
- DELIVERABLES_RAW (for packager)
  - list of deliverable items {TITLE, BODY, META(optional)}
- CHECK_REPORT updates (optional)
  - WARN/FAILED notes when boundaries are hit

User-facing output is emitted via COR.RELEASE_PACKAGER.

---

## [M] COMPATIBILITY BOUNDARIES
Supported production tasks (adapter scope):
- Prompt pack drafting (music/video generation prompts) with structure + constraints
- Lyrics drafting as original paraphrased/transformative text blocks (no verbatim copying)
- Album/EP blueprinting (themes, sonic palette, track roles, differentiation rules)
- Release pack metadata (tags, structure, naming placeholders)
- Consistency guardrails (anti-repetition, motif rotation)

Not supported (must route to domain pipes or governance):
- Canonical creation of album entities, passports, registry/index updates
- Bulk scraping or verbatim replication of copyrighted lyrics or protected texts
- Exact imitation of a living artist’s voice or identifiable style cloning as a requirement
- Mass generation beyond anti-noise caps without STEP_RUN batching

---

## [M] LEGACY PROFILE MAP
### PROD_DEFAULT
- Output: prompt pack + short lyrics skeleton + constraints checklist
- Noise: low
- Use: early exploration, quick iteration

### PROD_RELEASE
- Output: release-ready pack (prompt pack + lyrics draft + QA checks + metadata)
- Noise: medium (bounded)
- Use: preparing a track/album batch for publishing workflow

### PROD_SCALE
- Output: scalable album-series blueprint + variation rules + packaging templates
- Noise: medium (bounded)
- Use: designing 10–30 album lines without sameness

MODE_HINT mapping:
- FAST -> PROD_DEFAULT
- RELEASE_READY -> PROD_RELEASE
- MASTERPIECE -> PROD_RELEASE (plus deeper QA), not more noise

---

## [M] STEP-RUN BEHAVIOR (adapter rules)
Aligns to UE_V2 cadence and never bypasses COR.STEP_RUN_CONTROLLER.

S0) Intake mirror (read-only)
- Reuse normalized inputs from COR.TASK_INTAKE where available.
- If TASK_TEXT missing -> STOP (fail-handler semantics).

S1) Route confirmation
- Verify ROUTE_TOKEN permits legacy production adapter.
- If not permitted -> GAP ("legacy not permitted") and stop.

S2) Plan build
- Select legacy_profile (LEGACY_HINT or derived from MODE_HINT).
- Apply budgets:
  - Deliverables per step: 1–3 max
  - Lines per lyrics draft step: 16–40 max (bounded)
  - Prompt variants per step: 1–4 max
- Decide vocal policy (if constraints missing):
  - Default: 1 lead voice, optional backing layers as arrangement notes (not identity cloning).

S3) Produce deliverables for current "го"
- Emit only current-step deliverables with canonical titles.
- Maintain deterministic ordering and stable field names.

---

## [M] DELIVERABLE SHAPES (canonical titles)
Allowed DELIVERABLES_RAW titles:

- "PROD_CONSTRAINTS"
  - platform, duration_target, structure, language, voice_count, taboo list

- "PROMPT_PACK"
  - 1–4 prompt variants, each with:
    - GENRE_CORE, BPM_RANGE(optional), MOOD, INSTRUMENT_PALETTE, ARRANGEMENT_NOTES, VOCAL_NOTES, MIX_NOTES, STRUCTURE

- "LYRICS_DRAFT"
  - Original text only.
  - Must avoid obvious repeated phrases across drafts (anti-fingerprint rule).

- "ALBUM_BLUEPRINT"
  - theme, sonic palette, track roles, differentiation keys, motif rotation table

- "QA_CHECKLIST"
  - repeat-phrase scan rules, recognizability risk checks, structure validation

- "NEXT_STEP_QUEST"
  - one deterministic next prompt for the user

If WARN/GAP/STOP:
- Only "NEXT_ACTION" with minimal instruction.

---

## [M] ANTI-RECOGNIZABILITY / ANTI-REPETITION RULESET
- No verbatim sourcing:
  - Never include direct lines copied from protected or identifiable sources.
- Paraphrase with divergence:
  - If using public-domain inspirations, rewrite with structural divergence:
    - change imagery chain, replace metaphors, swap narrative voice, invert cadence
- Phrase blacklist (run-local):
  - Maintain a small run-local blacklist of standout phrases to avoid repeating within the batch.
- Cadence rotation:
  - Rotate line lengths and rhyme density across tracks to reduce template signature.
- Motif pool rotation:
  - Use a controlled pool (light, metal, water, dust, glass, wind, wire, ash) and rotate per album.

---

## [M] SAFETY / COMPLIANCE NOTES
- Copyright:
  - Do not output copyrighted lyrics or close paraphrases that remain recognizable.
  - If user demands exact imitation or near-copying, STOP.
- Voice identity:
  - Do not generate instructions to clone a specific identifiable singer’s voice.
- Harm:
  - No guidance enabling wrongdoing or targeted harassment.

(User-facing phrasing handled by COR.FAIL_HANDLER.)

---

## [M] ERROR HANDLING (adapter-level)
- Unsupported mandatory request -> GAP (missing pipe) or STOP (blocked), depending on REQUIRED_CHECKS.
- Missing REQUIRED_IDX access -> GAP (dependency missing).
- Safety boundary triggered -> STOP.
- Over-budget request -> WARN and downshift:
  - fewer prompts, shorter lyrics draft, stricter blueprint

Module emits structured signals; COR.FAIL_HANDLER produces the user-facing explanation.

---

## [M] GATES
PASS if:
- RAW-only, minimal load, step-run satisfied
- DELIVERABLES_RAW created using canonical titles
- Anti-recognizability rules applied (no verbatim, low fingerprint)

WARN if:
- Legacy fallback used while a domain pipe exists but not selected (must be logged)
- High similarity risk detected (requires rewrite pass)

GAP if:
- Required legacy keys/idx missing
- Legacy adapter not permitted by route token

STOP if:
- TASK_TEXT missing
- Copyright/identity cloning requested as mandatory
- Safety boundary blocks execution
