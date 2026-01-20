# CTL — CREDITS & METADATA POLICY (MUSIC) (CANON)

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 40_CTL__CONTROLLERS
FAMILY: 10_MUSIC_CONTROLLERS
LEVEL: L2
DOC_TYPE: CTL (CONTROLLER)
ENTITY_TYPE: CONTROLLER
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUSIC.CREDITS_METADATA_POLICY.001
OWNER: SYSTEM
ROLE: Enforce minimum viable credits/metadata blocks for track release documents and release packs. Ensures rights-safe attribution, consistent naming, and platform-ready fields. Prevents publishing without required metadata.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Standardized credits/metadata: required fields, provenance hooks for non-user lyrics, and deterministic CTL verdict."
- REASON: "Release docs without metadata break distribution and create rights ambiguity."
- IMPACT: "Every release artifact becomes publishable and validator-ready."
- CHANGE_ID: UE.CHG.2026-01-20.CTL.CREDITS.001

---

## 0) PURPOSE (LAW)
Эта политика гарантирует, что любые документы релиза содержат:
- корректные метаданные трека (title/artist/brand/version)
- кредиты (кто автор/исполнитель/продюсер/лирика)
- права/источники текста, если использован corpus (KB provenance)

Нельзя выпускать релиз без метаданных.

---

## 1) ABSOLUTE RULES
### 1.1 Required metadata block
Если документ относится к публикации трека (release), в нём обязателен METADATA блок.

### 1.2 Required credits block
CREDITS блок обязателен и не может быть пустым.

### 1.3 Rights clarity for lyrics
Если LYRICS_MODE = CORPUS или использованы non-user строки:
- обязателен RIGHTS/PROVENANCE блок (см. 5.3)
и он должен соответствовать KB Source Lock.
Иначе → FAIL.

### 1.4 Deterministic verdict
CTL возвращает CTL_VERDICT (см. 7). FAIL блокирует упаковку/публикацию.

---

## 2) APPLICABILITY
### 2.1 Artifact types (minimum)
- MUSIC_TRACK_RELEASE
- MUSIC_RELEASE_PACK

### 2.2 Invocation points
- RELEASE_PACK_ORC (перед финальной упаковкой)
- TRACK_TEST_DOC_GATE_ORC (если матрица требует)

---

## 3) REQUIRED REFERENCES (RAW)
KB SOURCE LOCK / NO FANTASY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/12__KB_SOURCE_LOCK_NO_FANTASY.md

PROMPT CONTRACT (context for lyrics mode)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md

RELEASE PACK ORC (consumer)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

---

## 4) REQUIRED METADATA (MINIMUM)
Документ релиза обязан содержать блок:

### 4.1 METADATA (required fields)
- TRACK_UID (or placeholder)
- TRACK_TITLE
- ARTIST_NAME (group)
- BRAND_NAME (label/brand)
- ALBUM_NAME (optional if single)
- RELEASE_DATE (planned/actual)
- VERSION_TAG (e.g., v1, v2, clean, alt, shorts)
- LANGUAGE (if any)
- GENRE_STYLE (short)

Если поля отсутствуют → FAIL (marker not confirmed).

---

## 5) REQUIRED CREDITS & RIGHTS (MINIMUM)
### 5.1 CREDITS (required fields)
- MUSIC_BY (composer/producer or “system-generated” if policy allows wording)
- LYRICS_BY
- VOCALS (who/what persona; can be “AI vocal performance” wording)
- MIX_MASTER (if applicable)
- ARTWORK (if applicable)
- NOTES (optional)

CREDITS не должен быть пустым.

### 5.2 LYRICS_MODE declaration (required)
- LYRICS_MODE: ORIGINAL | CORPUS | INSTRUMENTAL

### 5.3 RIGHTS / PROVENANCE (required when CORPUS)
Если LYRICS_MODE = CORPUS:
- KB_SOURCE_RAW
- SOURCE_STATUS: PD_CONFIRMED | LICENSE_CONFIRMED
- SOURCE_NOTE
- FULL_TEXT_ALLOWED (if full text used)

Если нет → FAIL (marker not confirmed / policy violation).

### 5.4 ORIGINAL lyrics
Если LYRICS_MODE = ORIGINAL:
- RIGHTS note must state: “Original text (user/system)”
- provenance not required

### 5.5 INSTRUMENTAL
Если INSTRUMENTAL:
- LYRICS_BY may be “N/A”
- RIGHTS block optional

---

## 6) REQUIRED CHECKS (DETERMINISTIC)
### CHECK A — Metadata present
Все поля 4.1 присутствуют.
Иначе → FAIL (marker not confirmed)

### CHECK B — Credits present
CREDITS блок присутствует и заполнен.
Иначе → FAIL (marker not confirmed)

### CHECK C — Lyrics mode declared
LYRICS_MODE ∈ {ORIGINAL, CORPUS, INSTRUMENTAL}
Иначе → FAIL (policy violation)

### CHECK D — Corpus rights compliance
Если CORPUS:
- присутствует provenance блок 5.3
- SOURCE_STATUS допустим
Иначе → FAIL (marker not confirmed / policy violation)

### CHECK E — No external claims without KB
Если в RIGHTS/NOTES встречаются источники без KB_SOURCE_RAW → FAIL (policy violation)

---

## 7) CTL VERDICT FORMAT (REQUIRED)
- CTL_ID: UE.CTL.MUSIC.CREDITS_METADATA_POLICY.001
- TARGET_ARTIFACT_TYPE: (MUSIC_TRACK_RELEASE | MUSIC_RELEASE_PACK | OTHER)
- TARGET_RAW: (raw link)
- VERDICT: PASS | FAIL
- FINDINGS:
  - bullet list
- REQUIRED_FIXES:
  - bullet list (empty if PASS)
- FAIL_CLASS:
  - RAW missing | marker not confirmed | input absent | policy violation
- RETURN_TO:
  - default repair ORC RAW

Default return route:
RELEASE_PACK_ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

---

## 8) CHANGE POLICY (LOCK)
- Менять обязательные поля только PATCH
- Если меняются требования к типам артефактов — синхронизировать Validation Matrix
- Права/кредиты должны быть согласованы с `CREDITS_RIGHTS_VAL` (validator)

---

END.
