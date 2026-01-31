SCOPE: Universe Engine (UE_V2)
DOC_TYPE: TEMPLATE_PACK
UID: UE.V2.TPL.NAV.STACK.015
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)

---

## TEMPLATE A) 00__<FOLDER>__INDEX_MANIFEST.md
SCOPE: UE_V2 / <FOLDER>
DOC_TYPE: INDEX_MANIFEST
UID: UE.V2.IDX.<FOLDER>.MANIFEST.001
VERSION: 1.0.0
STATUS: ACTIVE
NAV_RULE: RAW allowed here

### [M] PURPOSE
Единая адресная книга папки: KEY → RAW + краткий смысл.

### [M] KEY RULES
- KEY уникален в пределах папки
- KEY машинный, короткий, стабильный
- Рекомендуемый формат: TYPE.NAME или DOMAIN.TYPE.NAME
  - пример: SPC.MIX_ENGINEER, KB.SUNO_RULES, PANEL.QUALITY_GATES

### [M] ENTRIES (TABLE)
| KEY | TYPE | RAW | STATUS | BRIEF |
|---|---|---|---|---|
| SPC.MIX_ENGINEER | SPC | <RAW_LINK> | ACTIVE | Микс, баланс, частоты, читаемость |
| KB.SUNO_RULES | KB | <RAW_LINK> | ACTIVE | Запрет восклицаний, требования к оригинальности |
| PIPE.MUSIC_DEFAULT | PIPE | <RAW_LINK> | ACTIVE | Базовый доменный пайп музыки |

### [M] RESOLUTION NOTE
PIPELINE_CONTRACT и START_NODE используют только KEY. RAW резолвится здесь.

---

## TEMPLATE B) 00__<FOLDER>__PIPELINE_CONTRACT.md
SCOPE: UE_V2 / <FOLDER>
DOC_TYPE: PIPELINE_CONTRACT
UID: UE.V2.PIPE.<FOLDER>.CONTRACT.001
VERSION: 1.0.0
STATUS: ACTIVE
NAV_RULE: NO RAW INSIDE

### [M] PURPOSE
Описать порядок действий и состав участников. Все обращения к файлам — через KEY из INDEX_MANIFEST.

### [M] INPUT TOKENS
- TASK_TEXT
- MODE_HINT (optional)
- constraints (optional)

### [M] REQUIRED KEYS
- REQUIRED:
  - SPC: [SPC.MIX_ENGINEER, ...]
  - KB: [KB.SUNO_RULES, ...]
  - PANELS: [PANEL.QUALITY_GATES, ...]

### [M] PIPE STEPS (STEP-RUN READY)
P0) Resolve keys via INDEX_MANIFEST
P1) Load 1–3 target files (minimum)
P2) Produce OUTPUT artifact
P3) Emit RUN tokens (RUN_LOG / DECISION_LOG / TOKEN_ARCHIVE references by ID)

### [M] OUTPUT
- ARTIFACT
- RUN_TOKENS summary
- NEXT: "го"

### [M] GATES
PASS: все REQUIRED KEYS резолвятся
GAP: любой REQUIRED KEY отсутствует в INDEX_MANIFEST

---

## TEMPLATE C) 00__<FOLDER>__START_NODE.md
SCOPE: UE_V2 / <FOLDER>
DOC_TYPE: START_NODE
UID: UE.V2.STARTNODE.<FOLDER>.001
VERSION: 1.0.0
STATUS: ACTIVE
NAV_RULE: NO RAW INSIDE

### [M] PURPOSE
Локальная старт-капсула домена/папки. Дает минимум для правильного старта “в середине пирамиды”.

### [M] DEFAULTS
- DOMAIN: <FOLDER>
- EXEC_MODE_DEFAULT: STEP-RUN
- DEFAULT_PIPE_ID: PIPE.<FOLDER>_DEFAULT (KEY, не RAW)

### [M] REQUIRED_IDX_LOCAL (KEYS ONLY)
- MANIFEST: <FOLDER>.INDEX_MANIFEST (KEY)
- OPTIONAL: <FOLDER>.REG, <FOLDER>.XREF, <FOLDER>.KB (если реально нужно)

### [M] FIRST_STEP_PROMPT
го

### [M] GAP / STOP
GAP если:
- нет INDEX_MANIFEST
- нет DEFAULT_PIPE_ID в INDEX_MANIFEST
