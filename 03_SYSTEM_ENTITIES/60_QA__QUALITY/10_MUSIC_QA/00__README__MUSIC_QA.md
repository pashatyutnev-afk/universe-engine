# MUSIC QA (QUALITY) — REALM README (CANON)

FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/00__README__MUSIC_QA.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 60_QA__QUALITY
FAMILY: 10_MUSIC_QA
DOC_TYPE: README (FAMILY)
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.QA.MUSIC.REALM.README.001
OWNER: SYSTEM
ROLE: Canonical usage contract for music QA gates. Defines matrix-driven QA selection, verdict format, and how QA integrates into ORC pipelines after CTL+VAL.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt MUSIC_QA README as deterministic QA contract aligned with Validation Matrix + ORC flows; added standard QA verdict format."
- REASON: "Remove ambiguity: QA must be selected and applied deterministically, and its outcomes must be auditable."
- IMPACT: "Music outputs pass consistent acceptance gates; FAIL routes back to producing ORC without guessing."
- CHANGE_ID: UE.CHG.2026-01-20.QA.MUSIC.README.001

---

## 0) WHAT IS QA (IN MUSIC)
QA — приемка/гейты качества.  
QA проверяет “готово ли выпускать/паковать”, а не “соответствует ли правилам” (это VAL).

QA НЕ ДЕЛАЕТ:
- не создаёт контент,
- не заменяет CTL/VAL,
- не назначает владельцев (ORC→SPC),
- не выбирает пайплайны (PIPELINES map),
- не добавляет обязательные гейты без PATCH матрицы.

---

## 1) ABSOLUTE RULES
### 1.1 Matrix-driven QA selection
Какие QA-гейты обязательны — определяется `VALIDATION_MATRIX` по ARTIFACT_TYPE.

### 1.2 Placement order
QA всегда после CTL и VAL:
READINESS_CHECK_CTL → required CTL → required VAL → required QA → DOC_CONTROL

### 1.3 RAW-only navigation
Только RAW ссылки.

### 1.4 Output format is mandatory
Каждый QA гейт должен выдавать QA_VERDICT в стандартном формате.

---

## 2) REQUIRED REFERENCES (RAW)
VALIDATION MATRIX (required gates per artifact type)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md

PIPELINES (intent → pipeline selection)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md

---

## 3) HOW ORC USES QA (CANON FLOW)
1) ORC определяет ARTIFACT_TYPE (CARD | PROMPT | RELEASE | PACK | SPEC)
2) ORC читает `VALIDATION_MATRIX` и получает REQUIRED_QA
3) ORC применяет REQUIRED_QA к артефакту после CTL+VAL
4) QA возвращает:
   - VERDICT (PASS/WARN/FAIL)
   - SCORES (если применимо)
   - FAIL_REASONS / FIX_GUIDE
5) FAIL → возврат в producing ORC (обычно ALBUM→TRACK или RELEASE_PACK) и повтор QA после исправления

---

## 4) QA VERDICT FORMAT (REQUIRED)
Каждый QA результат должен содержать минимум:

- QA_CHECK_ID: (file/uid of QA gate)
- ARTIFACT_TYPE: (CARD | PROMPT | RELEASE | PACK | SPEC)
- TARGET_RAW: (raw link to the checked artifact)
- VERDICT: PASS | WARN | FAIL
- SCORE: (0-100 or N/A)
- REASONS: bullet list (concise)
- FIX_REQUIRED: bullet list
- RETURN_TO: (which ORC pipeline should repair; raw link)

---

## 5) MUSIC QA INVENTORY (CANON LIST, RAW)
00 — MUSIC QA README (this doc)

01 — SCROLL STOP 5S QA  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md

02 — LOOP 15S QA  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/02__LOOP_15S_QA.md

03 — RECOGNITION 10S QA  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/03__RECOGNITION_10S_QA.md

04 — CREATOR PANEL QA  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/04__CREATOR_PANEL_QA.md

05 — MIX TRANSLATION QA  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/05__MIX_TRANSLATION_QA.md

06 — HOOK PANEL QA  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/06__HOOK_PANEL_QA.md

07 — CATALOG DIFFERENTIATION QA  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/07__CATALOG_DIFFERENTIATION_QA.md

08 — VOICE DIVERSITY AUDIT QA  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/08__VOICE_DIVERSITY_AUDIT_QA.md

09 — REGRESSION GUARD QA  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/09__REGRESSION_GUARD_QA.md

---

## 6) COMMON RETURN ROUTES (CANON)
- Fix track artifacts (CARD/PROMPT/RELEASE):
  - return_to: ALBUM_TO_TRACK ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

- Fix release packaging:
  - return_to: RELEASE_PACK ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

- Re-run doc readiness:
  - return_to: TRACK_TEST_DOC_GATE ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

---

## 7) CHANGE POLICY (LOCK)
- Любые изменения QA-гейтов: PATCH + CHANGE_NOTE.
- Чтобы сделать QA-гейт обязательным для типа артефакта — сначала PATCH `VALIDATION_MATRIX`.

---

END.
