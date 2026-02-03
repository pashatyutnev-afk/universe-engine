FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/02__COR__DOMAIN_DETECTOR__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.DOMAIN_DETECTOR
UID: UE.V2.ENT.ORC.COR.DOMAIN_DETECTOR.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: Resolve via INDEX_MANIFEST (KEY->RAW)

---

## [M] ROLE
Domain detection and routing hint module.
Derives DOMAIN + ARTIFACT_TYPE candidates from normalized REQUEST and produces deterministic routing hints for ROUTE_TOKEN builder.

## [M] PURPOSE
- Identify the most likely DOMAIN (realm/category) of the task without loading other files.
- Identify ARTIFACT_TYPE (what user wants to get as a result).
- Produce a compact ROUTING_HINTS object used by `COR.ROUTE_TOKEN_BUILDER`.
- Keep everything deterministic and noise-free.

## [M] HARD_RULES
- No external loading, no cross-realm lookups, no RAW output.
- Do not invent user constraints; only classify what is present in REQUEST.
- Deterministic scoring: same input -> same candidates and scores.
- Output must be short and structured (ANTI_NOISE).
- MODE is USAGE-ONLY: no repo edits.

## [M] INPUTS
- REQUEST envelope from `COR.TASK_INTAKE` (required)
  - TASK_TEXT
  - MODE_HINT
  - CONSTRAINTS
  - INTENT_SIGNALS
- OPTIONAL: ROUTER_HINTS (if caller supplies additional signal flags)

## [M] OUTPUTS
- ROUTING_HINTS
  - DOMAIN_PRIMARY: string (may be "UNKNOWN" if insufficient signal)
  - DOMAIN_CANDIDATES: [{domain, score, reason}] (top 3 max)
  - ARTIFACT_TYPE: string
  - ARTIFACT_CANDIDATES: [{type, score, reason}] (top 3 max)
  - PIPE_SUGGESTION: string | null (only suggestion, not a decision)
  - REQUIRED_IDX_SUGGESTION: string | null (key/name only; resolution later)
  - REQUIRED_CHECKS_SUGGESTION: [string] (max 6)
- RUN_SEED update
  - NEXT_MODULE_KEY: COR.ROUTE_TOKEN_BUILDER
  - NEXT_PROMPT: "го"
- STATUS: PASS | FAIL
- FAIL_CODE + REQUIRED_FIX (when FAIL)

---

## [M] CLASSIFICATION TAXONOMY (v1)

### [M] ARTIFACT_TYPE (what to build)
Allowed types (canonical):
- PROMPT_PACK (prompts / instructions pack)
- LYRICS_PACK (song lyrics / text pack)
- BRAND_DNA (identity / DNA definition)
- ALBUM_PLAN (album lineup / differentiation map)
- DOC (markdown doc / spec / index)
- CODE (scripts / html / js / etc.)
- OTHER (fallback)

### [M] DOMAIN (where it belongs)
Domain is a routing tag, not a final realm decision.
Allowed domains (canonical minimal set):
- MUSIC
- VIDEO
- DESIGN
- BUSINESS
- REPO_GOVERNANCE
- REPO_NAV
- REPO_LOG
- OTHER
- UNKNOWN

---

## [M] DETECTION LOGIC (DETERMINISTIC)

### D0) Preconditions
- If REQUEST.TASK_TEXT missing or empty -> FAIL.INPUT_MISSING

### D1) Extract signals (no guessing)
From TASK_TEXT + CONSTRAINTS keys:
- tokens (lowercased, trimmed)
- presence flags:
  - mentions_music: ("трек", "трэки", "альбом", "музыка", "бит", "вокал", "лирика", "суно", "suno")
  - mentions_video: ("видео", "veo", "кадр", "сцена", "шот", "8 секунд", "fps", "рендер")
  - mentions_repo: ("ue_v2", "индекс", "орк", "orchestrator", "raw", "nav", "manifest", "uid", "лог")
  - mentions_brand: ("днк", "бренд", "айдентика", "позиционирование", "название", "tone", "стиль группы")
  - mentions_code: ("код", "html", "css", "js", "скрипт", "worker", "api")
- constraints flags:
  - has_duration (already present in REQUEST.INTENT_SIGNALS)
  - has_platform (REQUEST.CONSTRAINTS.platform exists)
  - has_refs (REQUEST.CONSTRAINTS.references exists)

### D2) ARTIFACT_TYPE scoring (0..100)
Rules (sum, capped at 100):
- +55 PROMPT_PACK if mentions "prompt/промпт/veo/suno" OR "собери промпт"
- +55 LYRICS_PACK if mentions "текст", "куплет", "припев", "лирика"
- +55 ALBUM_PLAN if mentions "20 альбомов", "план альбомов", "дискография"
- +55 BRAND_DNA if mentions "ДНК", "айдентика", "позиционирование"
- +55 DOC if mentions "док", "спека", "индекс", "manifest", "README"
- +55 CODE if mentions code tokens
Tie-break (deterministic):
1) Highest score wins
2) If tie: prefer DOC > BRAND_DNA > ALBUM_PLAN > PROMPT_PACK > LYRICS_PACK > CODE > OTHER
If all scores 0 -> ARTIFACT_TYPE = OTHER

### D3) DOMAIN scoring (0..100)
Rules:
- MUSIC: +70 if mentions_music, +20 if ARTIFACT_TYPE in {LYRICS_PACK, ALBUM_PLAN, BRAND_DNA} and music tokens exist
- VIDEO: +70 if mentions_video, +20 if ARTIFACT_TYPE == PROMPT_PACK and video tokens exist
- REPO_GOVERNANCE: +80 if mentions_repo AND tokens include governance cues ("gov", "rule", "compliance", "audit")
- REPO_NAV: +80 if mentions_repo AND tokens include nav cues ("nav", "index", "raw", "manifest")
- REPO_LOG: +80 if mentions_repo AND tokens include log cues ("log", "decision", "run_log")
- DESIGN: +60 if mentions_brand but no music/video tokens
- BUSINESS: +60 if mentions "продажи", "маркетинг", "стратегия", "магазин", "клиенты"
Tie-break:
1) Highest score wins
2) If tie: prefer REPO_* over MUSIC/VIDEO when mentions_repo true
3) Else prefer MUSIC over VIDEO if both present and ARTIFACT_TYPE not PROMPT_PACK
If no domain gets >=50 -> DOMAIN_PRIMARY = UNKNOWN and provide candidates with low scores.

### D4) PIPE_SUGGESTION (hint only)
- If DOMAIN_PRIMARY == MUSIC -> "PIPE.MUSIC_DEFAULT" (hint string; resolved later)
- If DOMAIN_PRIMARY == VIDEO -> "PIPE.VIDEO_DEFAULT"
- If DOMAIN_PRIMARY startswith "REPO_" -> "PIPE.REPO_DEFAULT"
- Else null

### D5) REQUIRED_IDX_SUGGESTION (hint only)
- If DOMAIN_PRIMARY in {REPO_GOVERNANCE, REPO_NAV, REPO_LOG} -> "IDX.REPO.ROOT"
- If DOMAIN_PRIMARY == MUSIC -> "IDX.MUSIC.ROOT"
- If DOMAIN_PRIMARY == VIDEO -> "IDX.VIDEO.ROOT"
- Else null
(Resolution is responsibility of router/token builder via NAV and available IDX sets.)

### D6) REQUIRED_CHECKS_SUGGESTION (max 6)
Always include minimal core checks:
- "CHECK.NAV.RAW_ONLY"
- "CHECK.ANTI_NOISE.MIN_LOAD"
- "CHECK.LOG.HOOKS_PRESENT"
Then domain-specific:
- MUSIC: "CHECK.IP.SAFETY_NO_DERIVATIVE_TEXT", "CHECK.DUPLICATES.AVOID_REPEATS"
- VIDEO: "CHECK.DURATION.FRAMES", "CHECK.STYLE.COHERENCE"
- REPO_*: "CHECK.MARKERS.MUST_LOAD", "CHECK.KEYS.RESOLVE_VIA_INDEX"

---

## [M] FAIL CONDITIONS
FAIL.INPUT_MISSING:
- REQUEST missing or REQUEST.TASK_TEXT empty
REQUIRED_FIX: Provide TASK_TEXT (what to do).

FAIL.REQUEST_MALFORMED:
- REQUEST envelope missing required fields produced by intake
REQUIRED_FIX: Re-run intake or provide normalized REQUEST.

---

## [M] ANTI_NOISE POLICY (MODULE)
- Output only ROUTING_HINTS + RUN_SEED + STATUS (+ FAIL details if needed).
- DOMAIN_CANDIDATES and ARTIFACT_CANDIDATES: top-3 only.
- Reasons: one short clause each.

---

## [M] OUTPUT TEMPLATE (CANON)

On PASS:
STATUS: PASS
ROUTING_HINTS:
  DOMAIN_PRIMARY: "<...>"
  DOMAIN_CANDIDATES:
    - { domain: "<...>", score: <0..100>, reason: "<short>" }
  ARTIFACT_TYPE: "<...>"
  ARTIFACT_CANDIDATES:
    - { type: "<...>", score: <0..100>, reason: "<short>" }
  PIPE_SUGGESTION: "<string|null>"
  REQUIRED_IDX_SUGGESTION: "<string|null>"
  REQUIRED_CHECKS_SUGGESTION: ["<...>", "<...>"]
RUN_SEED:
  NEXT_MODULE_KEY: COR.ROUTE_TOKEN_BUILDER
  NEXT_PROMPT: "го"

On FAIL:
STATUS: FAIL
FAIL_CODE: FAIL.<...>
REQUIRED_FIX: "<one line>"
NEXT_PROMPT: "го"

---

## [M] GATES
PASS if:
- DOMAIN_PRIMARY set (or UNKNOWN with candidates)
- ARTIFACT_TYPE set
- NEXT_MODULE_KEY = COR.ROUTE_TOKEN_BUILDER
- Output respects ANTI_NOISE

FAIL if:
- INPUT_MISSING or REQUEST_MALFORMED
