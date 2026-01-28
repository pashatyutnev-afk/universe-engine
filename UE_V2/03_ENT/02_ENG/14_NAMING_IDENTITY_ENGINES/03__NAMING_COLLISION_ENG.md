# Naming Collision Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/03__NAMING_COLLISION_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 14_NAMING_IDENTITY_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: NAMING_IDENTITY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.NAMING.NAMING_COLLISION.001
OWNER: SYSTEM
ROLE: Detects naming collisions (exact + normalized + near-duplicate) within a defined scope (group/album/global),
and outputs a collision report + safe approved shortlist.

Supports Release Pack safety and validator alignment.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Naming Collision engine: normalization rules, scope modes, decision outcomes, and output schema."
- REASON: "Naming collisions destroy catalog clarity and platform discoverability."
- IMPACT: "Cleaner catalog, fewer duplicates, safer titles for releases."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.NAMING.COLLISION.001

---

## 0) PURPOSE (LAW)
This engine answers:
**“Эти названия не пересекаются с тем, что уже есть?”**

It must:
- validate name candidates against catalog memory
- detect:
  - exact matches
  - normalized matches
  - near-duplicates (small edits)
- output:
  - PASS/WARN/BLOCK
  - approved shortlist
  - safe fallback titles
  - recommended fixes (suffix/prefix/word swap)

---

## 1) INPUTS (CONSUMES)
- Naming Brief (NB):
  - normalization rules and strictness
- Name Candidates Pack (NC)
- Catalog name memory snapshot (existing names):
  - group scope (default)
  - optional global scope (multi-group factory)
  - album scope (for track titles)

- Optional: Series rules (if series naming used)

---

## 2) OUTPUTS (PRODUCES)
Primary:
- NAMING_COLLISION_REPORT (NCR) — single SoT

Secondary:
- APPROVED_SHORTLIST (names cleared)
- BLOCKED_LIST (names rejected + why)
- SAFE_FALLBACKS (1–5 safe options)
- FIX_SUGGESTIONS (how to repair borderline names)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Naming Brief (NB)",
  "Name Candidates Pack (NC)",
  "Catalog Name Memory (scope)",
  "Series rules (optional)"
]
PRODUCES: [
  "Naming Collision Report (NCR)",
  "Approved shortlist",
  "Blocked list",
  "Safe fallbacks",
  "Fix suggestions"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/01__NAMING_BRIEF_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/02__NAMING_GENERATION_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/07__NAMING_COLLISION_VAL.md"
]
OUTPUT_TARGET: "05_PROJECTS//NAMING/COLLISIONS/"

---

## 4) SCOPE MODES (WHERE WE CHECK)
- SCOPE.GROUP (default)
- SCOPE.ALBUM (for track titles inside an album)
- SCOPE.GLOBAL (optional, multi-group factory)

Scope is chosen by orchestrator or by strictness level in NB.

---

## 5) NORMALIZATION RULES (STANDARD)
Use NB-provided rules. Default normalization includes:
- lowercase
- trim spaces
- collapse repeated spaces
- remove punctuation and symbols
- remove duplicate hyphens/underscores
- optional: remove stop-words (RU/EN)
- optional: simple transliteration handling (if MIX)

Normalized form is used for collision matching.

---

## 6) COLLISION TYPES
C1 — EXACT MATCH
- identical strings

C2 — NORMALIZED MATCH
- normalized forms match exactly

C3 — NEAR DUPLICATE
- very similar strings (small edit distance)
- same “core tokens” with minor changes
Examples:
- “Night Drive” vs “Night-Drive”
- “Тихий Город” vs “Город Тихий”

C4 — SERIES CONFLICT (optional)
- name violates series rules (e.g., wrong episode marker)

---

## 7) DECISION OUTCOMES
- PASS: candidate set has enough approved options; no hard collisions
- WARN: some collisions exist; still enough approved; requires fix suggestions
- BLOCK: too many collisions; no safe shortlist; must regenerate names or adjust brief

---

## 8) PROCEDURE (DETERMINISTIC)
1) Load NB (strictness + normalization rules + target type).
2) Load NC candidates from all buckets.
3) Load catalog name memory for selected scope.
4) Normalize all candidates and memory names.
5) For each candidate:
   - check C1 exact
   - check C2 normalized
   - check C3 near-duplicate using token overlap heuristic:
     - same 2+ key tokens OR same main noun phrase → near-duplicate
   - if series rules apply: check C4
6) Classify candidate:
   - APPROVED / WARN / BLOCKED
7) Build outputs:
   - Approved shortlist (top by score)
   - Blocked list with reasons
   - Fix suggestions for WARN names:
     - swap one token, change imagery token, add safe subtitle, add episode marker (if allowed)
8) Decide PASS/WARN/BLOCK at set level.

---

## 9) OUTPUT SCHEMA (MANDATORY)

### NAMING_COLLISION_REPORT (NCR)
- TARGET_TYPE:
- TARGET_UID:
- DATE:
- SCOPE_MODE:
- STRICTNESS:
- TOTAL_CANDIDATES:
- APPROVED_COUNT:
- WARN_COUNT:
- BLOCKED_COUNT:
- DECISION: {PASS | WARN | BLOCK}
- APPROVED_SHORTLIST:
  - name: reason (1 line)
- WARN_LIST:
  - name: collision_type + fix_suggestion
- BLOCKED_LIST:
  - name: collision_type + matched_existing_name
- SAFE_FALLBACKS:
  - list (1–5)
- NEXT_ACTION:
  - {PROCEED_TO_PLATFORM_FORMAT | APPLY_FIXES | REGENERATE}

---

## 10) FAILURE MODES & FIXES
1) Too strict → everything blocks
- Fix: reduce scope to GROUP; relax stop-word removal; widen allowed forms in Naming Brief.

2) Collisions slip through (false negatives)
- Fix: tighten near-duplicate heuristic; add token-based matching; log more memory names.

3) Overuse of generic names
- Fix: enforce must-signal identity in brief; strengthen imagery tokens.

---

## 11) HANDOFFS (XREF)
Feeds into:
- `14_NAMING_IDENTITY_ENGINES/04__PLATFORM_FORMAT_TITLES_ENG.md`
Used by:
- `11_MUSIC_FACTORY_ENGINES/06__RELEASE_PACK_ENG.md`

Validated by:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/07__NAMING_COLLISION_VAL.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
