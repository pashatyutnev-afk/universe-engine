# XREF MAP — PIPELINES (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: MAP
MAP_TYPE: PIPELINES
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.MAP.PIPELINES.001
OWNER: SYSTEM
ROLE: Deterministic pipeline selection (intent → pipeline). Defines primary ORC, required XREF maps, mandatory gate order, and expected output artifact types.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Initialized minimal canonical pipeline selection map for MUSIC routes + generic pipeline orchestrator route. No guessing, RAW-only."
- REASON: "Make routing deterministic and auditable, prevent implicit selection of ORC/owners/engines/gates."
- IMPACT: "System can select the correct ORC and enforce gates consistently for music production."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.PIPELINES.001

---

## 0) PURPOSE (LAW)
Эта карта отвечает на вопрос: “по intent задачи какой пайплайн запускать”.
Пайплайн = правила выбора ORC + обязательные зависимости + expected outputs.

---

## 1) ABSOLUTE RULES
### 1.1 RAW-only navigation
Навигация только по RAW.

### 1.2 Determinism
Если intent не матчится ни с одной записью → STOP: marker not confirmed (needs new pipeline record).

### 1.3 Mandatory dependencies
Каждый пайплайн обязан ссылаться на:
- ORC (primary)
- ORC→SPC ownership map
- ENG→ORC allowlist map
- Validation Matrix map

---

## 2) REQUIRED XREF MAPS (RAW)
ORC → SPC (ownership)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__MAP__ORC_to_SPC.md

ENG → ORC (allowlist)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__MAP__ENG_to_ORC.md

VALIDATION MATRIX
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md

---

## 3) REQUIRED CORE CONTROL (RAW)
READINESS CHECK (mandatory)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md

---

## 4) PIPELINE RECORD SCHEMA (CANON)
Каждая запись обязана иметь:
- PIPELINE_ID
- INTENT_KEYWORDS (comma list)
- PRIMARY_ORC_RAW
- PRIMARY_SPC_RULE (reference: use ORC→SPC map)
- REQUIRED_XREF (always the 3 maps in section 2)
- REQUIRED_GATES_ORDER (canonical order)
- OUTPUT_ARTIFACT_TYPES (comma list)
- NOTES

---

## 5) CANONICAL GATE ORDER (DEFAULT)
READINESS_CHECK_CTL → relevant VAL (by Validation Matrix) → relevant QA (by Validation Matrix) → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff

---

# 6) PIPELINES REGISTRY (MINIMUM CANON SET)

## 6.1 PIPELINE — GROUP → ALBUM
PIPELINE_ID: PIPE.MUSIC.GROUP_TO_ALBUM.001
INTENT_KEYWORDS: group setup, group foundation, create album blueprint, album plan, group-to-album
PRIMARY_ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md
PRIMARY_SPC_RULE: use ORC→SPC map for ORC_ID ORC.MUSIC.GROUP_TO_ALBUM.001
REQUIRED_XREF: ORC→SPC, ENG→ORC, VALIDATION_MATRIX
REQUIRED_GATES_ORDER: default (section 5)
OUTPUT_ARTIFACT_TYPES: PACKAGE
NOTES: Produces album blueprint pack and/or structured docs required for track production.

---

## 6.2 PIPELINE — ALBUM → TRACK
PIPELINE_ID: PIPE.MUSIC.ALBUM_TO_TRACK.001
INTENT_KEYWORDS: make track, track production, album-to-track, generate prompt, track card, track release
PRIMARY_ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md
PRIMARY_SPC_RULE: use ORC→SPC map for ORC_ID ORC.MUSIC.ALBUM_TO_TRACK.001
REQUIRED_XREF: ORC→SPC, ENG→ORC, VALIDATION_MATRIX
REQUIRED_GATES_ORDER: default (section 5)
OUTPUT_ARTIFACT_TYPES: MUSIC_TRACK_CARD, MUSIC_TRACK_PROMPT, MUSIC_TRACK_RELEASE
NOTES: Core track pipeline. All outputs must be documents, never bare chat content.

---

## 6.3 PIPELINE — TRACK TEST DOC GATE
PIPELINE_ID: PIPE.MUSIC.TRACK_TEST_DOC_GATE.001
INTENT_KEYWORDS: track doc gate, test doc, pre-release doc check, track readiness docs
PRIMARY_ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md
PRIMARY_SPC_RULE: use ORC→SPC map for ORC_ID ORC.MUSIC.TRACK_TEST_DOC_GATE.001
REQUIRED_XREF: ORC→SPC, ENG→ORC, VALIDATION_MATRIX
REQUIRED_GATES_ORDER: default (section 5)
OUTPUT_ARTIFACT_TYPES: SPEC, MAP, RUNBOOK
NOTES: Doc-gate pipeline. Used to enforce contracts and readiness on track documentation artifacts.

---

## 6.4 PIPELINE — RELEASE PACK
PIPELINE_ID: PIPE.MUSIC.RELEASE_PACK.001
INTENT_KEYWORDS: release pack, publish pack, pack release, prepare release, distribution pack
PRIMARY_ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md
PRIMARY_SPC_RULE: use ORC→SPC map for ORC_ID ORC.MUSIC.RELEASE_PACK.001
REQUIRED_XREF: ORC→SPC, ENG→ORC, VALIDATION_MATRIX
REQUIRED_GATES_ORDER: default (section 5)
OUTPUT_ARTIFACT_TYPES: MUSIC_RELEASE_PACK, PACKAGE
NOTES: Consolidates final track artifacts into a self-contained pack with working RAW pointers.

---

## 6.5 PIPELINE — PORTFOLIO PLANNER
PIPELINE_ID: PIPE.MUSIC.PORTFOLIO_PLANNER.001
INTENT_KEYWORDS: portfolio plan, release calendar, portfolio strategy, plan releases
PRIMARY_ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md
PRIMARY_SPC_RULE: use ORC→SPC map for ORC_ID ORC.MUSIC.PORTFOLIO_PLANNER.001
REQUIRED_XREF: ORC→SPC, ENG→ORC, VALIDATION_MATRIX
REQUIRED_GATES_ORDER: default (section 5)
OUTPUT_ARTIFACT_TYPES: SPEC, PACKAGE
NOTES: Planning-only pipeline. Produces structured planning artifacts; no audio outputs required.

---

## 6.6 PIPELINE — POET PACK
PIPELINE_ID: PIPE.MUSIC.POET_PACK.001
INTENT_KEYWORDS: poet pack, poem selection, PD corpus, lyrics source pack
PRIMARY_ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md
PRIMARY_SPC_RULE: use ORC→SPC map for ORC_ID ORC.MUSIC.POET_PACK.001
REQUIRED_XREF: ORC→SPC, ENG→ORC, VALIDATION_MATRIX
REQUIRED_GATES_ORDER: default (section 5)
OUTPUT_ARTIFACT_TYPES: PACKAGE, SPEC
NOTES: Selects/curates allowed poet materials and packages them as deterministic inputs.

---

## 6.7 PIPELINE — GENERIC ROUTING (AMBIGUOUS INTENT)
PIPELINE_ID: PIPE.CORE.ROUTING.DEFAULT.001
INTENT_KEYWORDS: ambiguous, unknown route, routing help, decide pipeline
PRIMARY_ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/05__PIPELINE_ORCHESTRATOR_ENG.md
PRIMARY_SPC_RULE: use ORC→SPC map for ORC_ID ORC.CORE.PIPELINE_ORCHESTRATOR.001
REQUIRED_XREF: ORC→SPC, ENG→ORC, VALIDATION_MATRIX
REQUIRED_GATES_ORDER: default (section 5)
OUTPUT_ARTIFACT_TYPES: RUNBOOK, MAP, SPEC, PACKAGE
NOTES: Used only when intent cannot be mapped. Must end by proposing a new explicit pipeline record.

---

## 7) EXTENSION POLICY (STRICT)
Чтобы добавить новый PIPELINE:
1) создать запись в этом файле (PATCH)
2) обеспечить существование ORC по RAW
3) обеспечить наличие ORC→SPC ownership (для этого ORC)
4) обеспечить ENG→ORC allowlist (для этого ORC)
5) обеспечить Validation Matrix coverage (artifact types)

---

END.
