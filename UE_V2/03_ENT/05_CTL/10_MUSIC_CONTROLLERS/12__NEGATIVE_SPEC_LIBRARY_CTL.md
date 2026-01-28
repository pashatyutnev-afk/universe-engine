# CTL — NEGATIVE SPEC LIBRARY (MUSIC) (CANON)

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md
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
UID: UE.CTL.MUSIC.NEGATIVE_SPEC_LIBRARY.001
OWNER: SYSTEM
ROLE: Enforce non-empty, structured negative specs in prompts and provide a canonical “negative library” baseline that reduces repetition, artifacts, and low-quality generations. Blocks empty negatives and uncontrolled drift.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Standardized negative spec: mandatory baseline set + structure + drift control. Added strict verdict and fix guidance."
- REASON: "Empty or random negatives cause quality collapse, repetition, and noisy artifacts."
- IMPACT: "Prompts become more stable across runs; regression is reduced; validators/QA gain consistent baseline."
- CHANGE_ID: UE.CHG.2026-01-20.CTL.NEGSPEC.001

---

## 0) PURPOSE (LAW)
Этот CTL:
1) заставляет каждый `MUSIC_TRACK_PROMPT` иметь NEGATIVE_SPEC (не пустой),
2) проверяет, что NEGATIVE_SPEC структурирован и содержит базовые запреты,
3) предотвращает “дрейф” негативов, когда каждый трек делает свой хаос.

---

## 1) ABSOLUTE RULES
### 1.1 Negative spec required
NEGATIVE_SPEC обязателен и не может быть пустым.

### 1.2 Baseline required
В NEGATIVE_SPEC обязан присутствовать BASELINE (минимальный набор запретов).
Если отсутствует → FAIL.

### 1.3 No contradictory negatives
NEGATIVE_SPEC не должен противоречить INTENT (например, запрет “no vocals” при LYRICS_MODE != INSTRUMENTAL).
Если противоречит → FAIL.

### 1.4 Deterministic verdict
CTL возвращает CTL_VERDICT (см. 7). FAIL блокирует пайплайн.

---

## 2) APPLICABILITY
### 2.1 Artifact types
- MUSIC_TRACK_PROMPT (minimum)
- MUSIC_RELEASE_PACK (если pack содержит “prompt variants”)

---

## 3) REQUIRED REFERENCES (RAW)
PROMPT CONTRACT (MUSIC)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md

(quality context)
REGRESSION_GUARD_QA  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/09__REGRESSION_GUARD_QA.md

---

## 4) NEGATIVE SPEC FORMAT (REQUIRED)
NEGATIVE_SPEC должен быть списком (bullets) и иметь структуру:

- BASELINE:
  - ...
- CONTENT_SAFETY (optional):
  - ...
- AUDIO_QUALITY:
  - ...
- ARRANGEMENT (optional):
  - ...
- VOCAL (conditional):
  - ...
- LYRICS (conditional):
  - ...
- STYLE_LOCK (optional):
  - ...

Разрешено:
- добавлять трек-специфичные запреты
Запрещено:
- удалять baseline
- превращать NEGATIVE_SPEC в одну строку “no bad stuff”

---

## 5) BASELINE LIBRARY (CANON MIN SET)
Это минимальный baseline, который обязан быть в каждом промпте (как смысловые запреты, без привязки к конкретной платформе):

### 5.1 BASELINE (mandatory bullets)
- avoid excessive repetition of the same line/phrase
- avoid unintelligible / mumbled vocals
- avoid clipping / distortion / harsh sibilance
- avoid random noise, glitches, artifacts
- avoid off-key / unstable pitch (unless explicitly desired)
- avoid chaotic structure (must follow section plan)
- avoid generic placeholder lyrics / nonsense syllables
- avoid abrupt ending (unless intentional)

### 5.2 Conditional baseline rules
Если LYRICS_MODE = INSTRUMENTAL:
- baseline must include: no lyrics / no vocal phrases

Если вокал обязателен (LYRICS_MODE != INSTRUMENTAL):
- baseline must NOT include “no vocals”

---

## 6) REQUIRED CHECKS (DETERMINISTIC)
### CHECK A — NEGATIVE_SPEC present and not empty
Если отсутствует/пустой → FAIL (marker not confirmed)

### CHECK B — BASELINE present
Если отсутствует блок BASELINE или он пустой → FAIL (marker not confirmed)

### CHECK C — Baseline contains minimum intents
Baseline должен покрывать минимум:
- repetition control
- intelligibility / vocal clarity
- audio artifacts/noise
- structure adherence

Если нет хотя бы одного — FAIL (policy violation)

### CHECK D — No contradictions
- LYRICS_MODE vs negatives
- VOCAL intent vs negatives
Если есть противоречие → FAIL (policy violation)

### CHECK E — Prompt contract consistency
Если это MUSIC_TRACK_PROMPT:
- NEGATIVE_SPEC должен соответствовать PROMPT_CONTRACT (не пустой, bullets)
Если нет → FAIL (marker not confirmed)

---

## 7) CTL VERDICT FORMAT (REQUIRED)
- CTL_ID: UE.CTL.MUSIC.NEGATIVE_SPEC_LIBRARY.001
- TARGET_ARTIFACT_TYPE: (MUSIC_TRACK_PROMPT | MUSIC_RELEASE_PACK | OTHER)
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

## 8) CHANGE POLICY (LOCK)
- Менять baseline только PATCH
- Если baseline становится обязательным для новых типов артефактов — синхронизировать Validation Matrix

---

END.
