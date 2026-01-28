# CTL — PROMPT CONTRACT (MUSIC) (CANON)

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md
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
UID: UE.CTL.MUSIC.PROMPT_CONTRACT.001
OWNER: SYSTEM
ROLE: Enforce deterministic prompt structure for MUSIC_TRACK_PROMPT. Ensures required fields exist, forbids external text without KB provenance, and outputs a strict CTL verdict trace compatible with ORC pipelines and validators.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Hardened MUSIC prompt contract: mandatory fields, KB provenance hooks, negative spec requirements, and strict CTL_VERDICT format."
- REASON: "Prevent unusable prompts, missing constraints, and rights-risk text injection."
- IMPACT: "All track prompts become machine-checkable, reproducible, and safe for catalog production."
- CHANGE_ID: UE.CHG.2026-01-20.CTL.PROMPT.001

---

## 0) PURPOSE (LAW)
Этот CTL проверяет, что `MUSIC_TRACK_PROMPT` соответствует контракту:
- структура и обязательные поля присутствуют
- негативные ограничения заданы
- если используется corpus text (не user original) — есть KB provenance и соблюдена PD политика
- промпт пригоден для downstream ORC (ALBUM→TRACK, DOC-GATE, RELEASE-PACK)

---

## 1) ABSOLUTE RULES
### 1.1 RAW-only navigation
Только RAW.

### 1.2 No external text without KB provenance
Если в промпте есть строки/выдержки/цитаты, которые не являются user original:
- обязателен provenance блок (см. 5)
- обязателен PD policy (см. 3.2)
Иначе → FAIL.

### 1.3 Deterministic contract
Промпт должен быть разложим на фиксированные поля (без “свалки текста”).
Если поля смешаны/невозможно проверить → FAIL.

### 1.4 Verdict must be explicit
CTL обязан возвращать CTL_VERDICT (см. 7). FAIL блокирует пайплайн.

---

## 2) APPLICABILITY
### 2.1 Target artifact type
- MUSIC_TRACK_PROMPT

### 2.2 Invocation points
- при создании/редактировании трека (ALBUM_TO_TRACK_ORC)
- при DOC-GATE (TRACK_TEST_DOC_GATE_ORC), если матрица требует

---

## 3) REQUIRED REFERENCES (RAW)

### 3.1 KB boundary law
KB SOURCE LOCK / NO FANTASY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/12__KB_SOURCE_LOCK_NO_FANTASY.md

### 3.2 Poetry policy hooks (if corpus used)
POET PD POLICY (CTL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md

PD ONLY (VAL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md

### 3.3 Recommended companion CTL
DURATION POLICY (CTL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md

NEGATIVE SPEC LIBRARY (CTL)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md

---

## 4) CONTRACT SHAPE (REQUIRED SECTIONS)
`MUSIC_TRACK_PROMPT` должен содержать минимум:

### 4.1 HEADER / META
- TRACK_UID (or placeholder)
- TRACK_TITLE
- GROUP (name/uid if known)
- ALBUM (name/uid if known)
- VERSION / STATUS / LOCK

### 4.2 INTENT
- GENRE_STYLE (short)
- MOOD_ENERGY (short)
- DIFFERENTIATION_NOTE (1–2 строки: чем отличается)
- LANGUAGE (if any)

### 4.3 STRUCTURE
- SECTION_PLAN (intro/verse/chorus/bridge/outro) или эквивалентный план
- HOOK_INTENT (коротко: где и какой хук)

### 4.4 VOCAL / PERFORMANCE (optional but recommended)
- VOICE_INTENT (gender/age/timbre vibe as text)
- DELIVERY_INTENT (soft/aggressive/whisper etc)

### 4.5 LYRICS MODE (REQUIRED)
Одно из:
- LYRICS_MODE: ORIGINAL (user original / new writing)
- LYRICS_MODE: CORPUS (poet/excerpts/mosaic)
- LYRICS_MODE: INSTRUMENTAL (no lyrics)

Если LYRICS_MODE = CORPUS → обязателен блок 5 (provenance).

### 4.6 NEGATIVE SPEC (REQUIRED)
- NEGATIVE_SPEC: список ограничений (bullet list)
Должен быть не пустым.

### 4.7 DURATION TARGET (REQUIRED)
- DURATION_TARGET (seconds or short range)
- HOOK_TIMING_INTENT (например: early hook)

---

## 5) CORPUS / PROVENANCE BLOCK (REQUIRED WHEN CORPUS)
Если LYRICS_MODE = CORPUS, в промпте обязателен блок:

- KB_SOURCE_RAW: raw link
- SOURCE_STATUS: PD_CONFIRMED | LICENSE_CONFIRMED
- SOURCE_NOTE: short
- FULL_TEXT_ALLOWED: present only if full text is used
- EXCERPTS: list of excerpts (short) or references to POET_PACK_SPEC items

Запрещено:
- вставлять corpus lines без KB_SOURCE_RAW
- писать “из такого-то стихотворения” без provenance markers

---

## 6) DETERMINISTIC CHECKS (WHAT THIS CTL ENFORCES)
### CHECK A — required sections exist
Поля 4.1, 4.2, 4.3, 4.5, 4.6, 4.7 присутствуют.
Иначе → FAIL (marker not confirmed).

### CHECK B — NEGATIVE_SPEC not empty
Если пусто → FAIL (policy violation).

### CHECK C — LYRICS_MODE is valid
Только ORIGINAL | CORPUS | INSTRUMENTAL.
Иначе → FAIL.

### CHECK D — CORPUS provenance present when needed
Если CORPUS и нет блока 5 → FAIL (marker not confirmed).

### CHECK E — No “external claims”
Если в тексте промпта встречается ссылка/источник без KB_SOURCE_RAW → FAIL (policy violation).

### CHECK F — duration declared
DURATION_TARGET обязан быть явным.  
Если отсутствует → FAIL.

---

## 7) CTL VERDICT FORMAT (REQUIRED)
Каждый запуск контроллера обязан вернуть:

- CTL_ID: UE.CTL.MUSIC.PROMPT_CONTRACT.001
- TARGET_ARTIFACT_TYPE: MUSIC_TRACK_PROMPT
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
ALBUM_TO_TRACK_ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

---

## 8) NOTES (STRICT)
- Этот CTL не “улучшает” промпт, а только проверяет контракт и блокирует несоответствия.
- Детальные правила длительности/негативов могут быть усилены отдельными CTL (см. 3.3).
- Если нужно расширить контракт полями (например, credits intent, platform intent) — делать PATCH этого CTL и синхронизировать Validation Matrix.

---

END.
