# ORC — RELEASE PACK (CANON)

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 20_ORC__ORCHESTRATORS
FAMILY: 10_MUSIC_ORCHESTRATORS
LEVEL: L2
DOC_TYPE: ORC (ORCHESTRATOR)
ENTITY_TYPE: ORCHESTRATOR
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ORC.MUSIC.RELEASE_PACK.001
OWNER: SYSTEM
ROLE: Deterministic pipeline: consolidate track artifacts into a release pack (self-contained), enforce required gates, and prepare for publication handoff.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt RELEASE_PACK ORC as strict contract: inputs/outputs, packaging rules, XREF dependencies, mandatory gates, and signoff chain."
- REASON: "Prevent incomplete packs and un-audited releases. Ensure navigation and credits consistency."
- IMPACT: "Release packs become deterministic and publish-ready with clear gate compliance."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.RPACK.001

---

## 0) PURPOSE (LAW)
Этот ORC собирает и упаковывает релиз (один трек или набор треков) в самодостаточный release pack.
Обязанности:
- выбрать состав пакета (что входит),
- проверить обязательные гейты по матрице,
- обеспечить навигационную целостность,
- оформить результат как документ-артефакт (PACKAGE).

---

## 1) ABSOLUTE LAWS
### 1.1 RAW-only navigation
Только RAW ссылки из ROOT LINK BASE или присланные пользователем.

### 1.2 Ownership is mandatory
Владельцы берутся только из `ORC → SPC` карты.

### 1.3 Allowlist engines only
Использовать ENG только по `ENG → ORC` allowlist.

### 1.4 Mandatory gate order
READINESS_CHECK_CTL → relevant VAL → relevant QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff

### 1.5 Package must be self-contained
Release pack не может быть “списком в чате”.
Это документ-артефакт, который:
- содержит явные RAW pointers на все элементы,
- содержит структуру, состав, версии, и правила публикации (если применимо),
- не имеет “битых ссылок”.

---

## 2) REQUIRED XREF (RAW)
PIPELINES (intent → pipeline)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md

ENG → ORC allowlist
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__MAP__ENG_to_ORC.md

ORC → SPC ownership
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__MAP__ORC_to_SPC.md

VALIDATION MATRIX
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md

---

## 3) REQUIRED CONTROL (RAW)
READINESS CHECK (mandatory)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md

MUSIC CTL FAMILY (policies)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/00__README__MUSIC_CONTROLLERS.md

---

## 4) INPUTS (MINIMUM)
### 4.1 Required
Один из вариантов:
A) Single Track Release
- MUSIC_TRACK_CARD (final)
- MUSIC_TRACK_PROMPT (final)
- MUSIC_TRACK_RELEASE (final)

B) Multi Track Release
- список треков, каждый с (CARD + PROMPT + RELEASE)

### 4.2 Optional context
- Brand context (если релиз привязан к бренду/лейблу)
- Album context (если релиз = часть альбома)
- Distribution targets (YouTube / streaming / etc) как метаданные (без внешних ссылок, только intent)

### 4.3 Stop rule
Если нет минимум одного трека с финальными артефактами → STOP: input absent

---

## 5) OUTPUTS (ARTIFACT SET)
- MUSIC_RELEASE_PACK (PACKAGE doc)
- OPTIONAL: per-track summary blocks (внутри пакета)
- OPTIONAL: publish checklist (если задан стандартом, иначе не изобретается)

Required gates for MUSIC_RELEASE_PACK берутся из `VALIDATION_MATRIX`.

---

## 6) PACKAGING RULES (STRICT)
### 6.1 Contents must be explicit
Пакет обязан перечислить:
- включённые треки (UID + title),
- RAW ссылки на card/prompt/release каждого трека,
- версии каждого файла (если указаны в файлах),
- кредиты/права (отсылка на политику, без переизобретения).

### 6.2 Navigation integrity
- все RAW ссылки должны открываться
- отсутствующие файлы = GAP → STOP: input absent (для комплекта)

### 6.3 Naming consistency
- единый стиль названий (group/album/track)
- отсутствие конфликтов имен (если выявляется → фиксируется в violations)

### 6.4 Variants
Если трек имеет варианты:
- перечислить вариант как отдельную запись (Variant_ID)
- привязать к RELEASE_VARIANTS_CTL (если используется)

---

## 7) PIPELINE STEPS (DETERMINISTIC)

### STEP 0 — PRECHECK (CTL)
Owner: PRIMARY_SPC (из ORC→SPC)  
Gate: READINESS_CHECK_CTL  
Input: состав релиза + ссылки на артефакты  
Output: PASS/FAIL

Fail → STOP (по CTL).

---

### STEP 1 — MANIFEST BUILD (SPC)
Owner: PRIMARY_SPC  
Input: список треков + их финальные артефакты  
Output:
- PACK_MANIFEST (таблица состава)
- MISSING_ITEMS list (если есть)

If missing → STOP: input absent

---

### STEP 2 — POLICY APPLICATION (CTL)
Owner: PRIMARY_SPC + CTL  
Apply:
- QUALITY_GATES_CTL
- FINGERPRINT_COLLISION_THRESHOLDS_CTL (если релиз требует анти-коллизии)
- CREDITS_METADATA_POLICY_CTL
- RELEASE_VARIANTS_CTL (если есть варианты)

Output:
- POLICIES_APPLIED (список)
- REQUIRED_QA_SET (ссылка на матрицу по типу MUSIC_RELEASE_PACK)

---

### STEP 3 — VALIDATION + QA (by matrix)
Owner: relevant VAL + relevant QA  
Rules:
- REQUIRED_VAL и REQUIRED_QA берутся из `VALIDATION_MATRIX` по ARTIFACT_TYPE = MUSIC_RELEASE_PACK
- дополнительно проверяются связи/битые ссылки/конфликты

Output:
- VIOLATIONS (if any)
- QA_VERDICT (PASS/WARN/FAIL)

FAIL → вернуть на STEP 1/2 (исправление состава/метаданных)

---

### STEP 4 — PACK DOCUMENT ASSEMBLY (SPC)
Owner: PRIMARY_SPC  
Output:
- MUSIC_RELEASE_PACK document (self-contained)
- внутри: manifest + ссылки + notes

---

### STEP 5 — DOC CONTROL + SIGNOFF
Owner: DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC  
Action:
- doc control fields, UID/version/naming compliance
- финальная подпись

Output:
- FINAL MUSIC_RELEASE_PACK

---

## 8) HANDOFFS (CANON)
- PRIMARY_SPC: сборка и решения по составу пакета
- CTL: политики и readiness
- VAL: фиксация нарушений
- QA: приемка по гейтам
- DOC_CONTROLLER_SPC: doc control проверка
- MACHINE_ARCHITECT_SPC: финальный signoff

---

## 9) EXTENSION POLICY (STRICT)
Если добавляем новый тип релиз-пакета или новые требования:
1) сначала обновить VALIDATION_MATRIX (PATCH)
2) затем обновить XREF maps (если нужно)
3) затем обновить этот ORC (PATCH)

---

END.
