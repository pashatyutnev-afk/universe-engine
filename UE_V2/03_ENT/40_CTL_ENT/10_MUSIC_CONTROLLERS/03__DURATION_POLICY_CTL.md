# CTL — DURATION POLICY (MUSIC) (CANON)

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md
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
UID: UE.CTL.MUSIC.DURATION_POLICY.001
OWNER: SYSTEM
ROLE: Enforce explicit duration targets and hook timing intent for track prompts and release packs. Prevents ambiguous runtime lengths and aligns with short-form QA gates.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Formalized duration policy: required DURATION_TARGET, hook timing intent, and allowed ranges for different release intents."
- REASON: "Without duration policy, prompts drift and QA gates become inconsistent."
- IMPACT: "Track outputs become comparable and short-form ready; ORC pipelines gain deterministic constraints."
- CHANGE_ID: UE.CHG.2026-01-20.CTL.DURATION.001

---

## 0) PURPOSE (LAW)
Эта политика заставляет каждый трек иметь:
- явную цель длительности (DURATION_TARGET)
- намерение тайминга хука (HOOK_TIMING_INTENT)

И запрещает расплывчатые “как получится”.

---

## 1) ABSOLUTE RULES
### 1.1 Explicit duration required
Если артефакт подразумевает генерацию/публикацию трека, DURATION_TARGET обязателен.
Если отсутствует → FAIL.

### 1.2 Hook timing intent required
HOOK_TIMING_INTENT обязателен для вокальных/лирик треков.
Если трек инструментальный — можно указать “instrumental hook” или “motif entry”.

### 1.3 Deterministic verdict
CTL выдаёт PASS/FAIL с требуемыми исправлениями.

---

## 2) APPLICABILITY
### 2.1 Artifact types (minimum)
- MUSIC_TRACK_PROMPT
- MUSIC_RELEASE_PACK (если пак собирает варианты/шортсы)

### 2.2 Invocation points
- ALBUM_TO_TRACK_ORC (на этапе промпта)
- RELEASE_PACK_ORC (на этапе упаковки, если есть variants)

---

## 3) REQUIRED REFERENCES (RAW)
PROMPT CONTRACT (MUSIC)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md

QA hooks (context):
SCROLL_STOP_5S_QA  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md

LOOP_15S_QA  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/02__LOOP_15S_QA.md

RECOGNITION_10S_QA  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/03__RECOGNITION_10S_QA.md

---

## 4) POLICY (ALLOWED TARGETS)
Политика задаёт “разрешённые” диапазоны по intent.
Если intent неизвестен — применяем DEFAULT.

### 4.1 DEFAULT (general track)
- DURATION_TARGET: 120–200s (2:00–3:20)

### 4.2 SHORT-FRIENDLY (platform short readiness)
- DURATION_TARGET: 90–150s (1:30–2:30)

### 4.3 UGC HOOK-FIRST
- DURATION_TARGET: 80–130s (1:20–2:10)

### 4.4 LONGFORM (rare)
- DURATION_TARGET: 180–260s (3:00–4:20)
Требует явного маркера:
- LONGFORM_ALLOWED: true (в артефакте)

---

## 5) HOOK TIMING POLICY
### 5.1 Required field
HOOK_TIMING_INTENT must be one of:
- EARLY (hook ≤ 0:15)
- MID (hook 0:16–0:35)
- LATE (hook > 0:35)
- INSTRUMENTAL_MOTIF (instrumental motif entry ≤ 0:20)

Если значение не из списка → FAIL.

### 5.2 Default
Если не указано, но трек вокальный/лирик → FAIL (не подставлять молча).

---

## 6) REQUIRED CHECKS (DETERMINISTIC)
### CHECK A — DURATION_TARGET present
- must be explicit seconds or range in seconds
If missing → FAIL_CLASS: marker not confirmed

### CHECK B — Range fits policy
- если DURATION_TARGET выходит за пределы выбранного режима и нет маркера LONGFORM_ALLOWED → FAIL_CLASS: policy violation

### CHECK C — HOOK_TIMING_INTENT valid
- must be enum from 5.1
Else → FAIL_CLASS: policy violation

### CHECK D — Consistency with prompt contract
- если артефакт MUSIC_TRACK_PROMPT — он обязан содержать DURATION_TARGET и HOOK_TIMING_INTENT также по PROMPT_CONTRACT
Если промпт контракт не соблюдён → FAIL (marker not confirmed)

---

## 7) CTL VERDICT FORMAT (REQUIRED)
- CTL_ID: UE.CTL.MUSIC.DURATION_POLICY.001
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
- Менять диапазоны/enum только PATCH
- Если меняется требование для типов артефактов — синхронизировать Validation Matrix

---

END.
