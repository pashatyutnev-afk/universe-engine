FILE: UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/09__MUS__TRACK_BUILD_STEP__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 03_MUSIC_ORC_ENT
DOC_TYPE: ENTITY_PASSPORT
DOMAIN: MUS_ORC_ENT
UID: UE.V2.ENT.ORC.MUS.TRACK_BUILD_STEP.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-04
OWNER: ORC_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: MUS_TRACK_BUILD_STEP
- ENTITY_CLASS: ORC
- UID: UE.V2.ENT.ORC.MUS.TRACK_BUILD_STEP.001

---

## [M] PURPOSE
Управляет пошаговой сборкой трека в step-run режиме: DRAFT → REVISE → FINAL.
Делает это детерминированно через ROUTE_TOKEN и PROMPT_PACK:
- фиксирует неизменяемые параметры (style/bpm/instruments/voice/structure),
- задаёт, что именно менять на каждом шаге,
- собирает EVIDENCE (что пробовали, что сработало),
- подаёт входы в фокус-лупы (hook/mix/lyrics) только когда есть критерии.

---

## [M] HARD_RULES
- STEP-RUN ONLY: выполняется строго по шагам, без пропусков.
- CONSTRAINT LOCK: на шаге REVISE и далее нельзя менять стиль и базовую опору, кроме случаев GAP/FAIL.
- ONE-DELTA: на каждом шаге меняем не более 1–2 осей (например: хук и барабаны, но не хук и стиль одновременно).
- EVIDENCE REQUIRED: каждый шаг обязан оставить артефакт результата и короткую оценку.
- NO EXCLAMATION: запрещён символ `!` в любом текстовом поле (prompts, lyrics, notes, logs).

---

## [M] INPUTS / OUTPUTS

### Inputs (required)
- ROUTE_TOKEN
- MUS_BRIEF
- STYLE_ROUTE_TOKEN
- PROMPT_PACK (from MUS.PROMPT_PACKAGER)
- MODE_HINT (optional): FAST | RELEASE_READY | MASTERPIECE

### Inputs (optional)
- LYRICS_FINAL (if vocal required)
- PRIOR_ATTEMPTS (history)
- USER_FEEDBACK (after audition)
- TOOL_CONSTRAINTS (platform, duration, stem availability)

### Outputs
- STEP_RESULT
  - step_id: DRAFT|REVISE|FINAL
  - prompt_used (main + negative)
  - lyrics_used (if any)
  - tool_settings_hint (if any)
  - result_summary (1–2 строки)
  - scorecard (mini)
  - next_step_recommendation
- BUILD_LOG_SNIPPET (for RUN_LOG / DECISION_LOG)
- FAIL_CODE (optional)
- GAP_NOTE (optional)

---

## [M] STEP MODEL (canonical)

### Step: DRAFT
Goal:
- получить 1–3 базовых варианта, проверить, что стиль и энергетика совпадают с brief

Locks:
- genre/substyle, bpm, primary instruments, vocal preference, language (если вокал)

Allowed changes:
- аранжировка (мелкие детали), вариант хука, плотность ударных, тембр синта

Deliverables:
- DRAFT_A (required)
- DRAFT_B (optional)
- quick_scorecard

Exit criteria:
- хотя бы один вариант попадает в рамку по стилю и энергии
- если нет, то FAIL или GAP в сторону MUS.GENRE_STYLE_ROUTER

### Step: REVISE
Goal:
- улучшить выбранный draft по 1–2 целевым осям (обычно hook или mix)

Locks:
- всё из DRAFT locks
- структура (если уже выбрана)
- вокальная манера и язык (если применимо)

Allowed changes:
- hook phrasing/melody contour
- drum tightness, bass balance
- clarity vs warmth
- lyric micro-edits (если есть вокал)

Deliverables:
- REVISE_1 (required)
- scorecard + notes what changed

Exit criteria:
- выбранный вариант имеет стабильный хук и нет критических микс-проблем
- если хук слабый → handoff в MUS.HOOK_FOCUS_LOOP
- если микс разваливается → handoff в MUS.MIX_FOCUS_LOOP
- если смысл/текст хромает → handoff в MUS.LYRICS_FOCUS_LOOP

### Step: FINAL
Goal:
- зафиксировать финальную версию, собрать релизный пакет доказательств

Locks:
- все locks из REVISE
- no new creative axes allowed, только стабилизация

Allowed changes:
- минимальная полировка, уровень энергии, чистка артефактов, финальная правка текста без смены смысла

Deliverables:
- FINAL_MASTER (required)
- FINAL_PROMPT_PACK (as used)
- FINAL_SCORECARD
- handoff пакет в MUS.RELEASE_ASSEMBLER и MUS.RELEASE_PACK

Exit criteria:
- QA gates проходят (см MUS.QA_CHECKS)
- metadata completeness OK

---

## [M] MODE_HINT BEHAVIOR

### FAST
- DRAFT: 1 вариант
- REVISE: 1 итерация
- FINAL: сразу, минимум артефактов, но EVIDENCE всё равно фиксируется

### RELEASE_READY
- DRAFT: 2 варианта
- REVISE: 1–2 итерации
- FINAL: обязательные QA и метаданные

### MASTERPIECE
- DRAFT: 3 варианта
- REVISE: до 3 итераций, подключать focus loops по триггерам
- FINAL: строгий evidence pack + стабилизация, без расширения scope

---

## [M] MINI SCORECARD (canonical)
Scorecard fields (0–5):
- hook_catchiness
- groove_energy
- mix_clarity
- low_end_control
- vocal_fit (if applicable)
- lyric_fit (if applicable)
- uniqueness
- replay_value

---

## [M] ROUTING TRIGGERS (handoff rules)
- If hook_catchiness < 3:
  - call MUS.HOOK_FOCUS_LOOP with locked constraints
- If mix_clarity < 3 or low_end_control < 3:
  - call MUS.MIX_FOCUS_LOOP with locked constraints
- If lyric_fit < 3:
  - call MUS.LYRICS_FOCUS_LOOP with locked constraints
- If style mismatch persists after DRAFT:
  - call MUS.GENRE_STYLE_ROUTER and rebuild PROMPT_PACK

---

## [M] BUILD_LOG SNIPPET (format)
BUILD_LOG_SNIPPET:
- route_token_id: <id>
- step_id: <DRAFT|REVISE|FINAL>
- locks:
  - genre/substyle: <..>
  - bpm: <..>
  - instruments: <..>
  - vocals/lang: <..>
  - structure: <..>
- changed_axes:
  - <axis1>
  - <axis2>
- result_summary: "<1–2 lines>"
- scorecard:
  - hook_catchiness: <0-5>
  - groove_energy: <0-5>
  - mix_clarity: <0-5>
  - low_end_control: <0-5>
  - replay_value: <0-5>
- next_action: "<stay|handoff:HOOK|handoff:MIX|handoff:LYRICS|reroute:STYLE>"

---

## [M] FAIL CONDITIONS
- FAIL_CODE: MUS.FAIL.TRACK_STEP.MISSING_PROMPT_PACK
  - нет PROMPT_PACK или он пустой
- FAIL_CODE: MUS.FAIL.TRACK_STEP.MISSING_ROUTE_TOKEN
  - нет ROUTE_TOKEN
- FAIL_CODE: MUS.FAIL.TRACK_STEP.LYRICS_REQUIRED_MISSING
  - brief требует вокал, но нет lyrics
- FAIL_CODE: MUS.FAIL.TRACK_STEP.INVALID_PUNCT
  - найден символ `!` после нормализации
- FAIL_CODE: MUS.FAIL.TRACK_STEP.NON_DETERMINISTIC_CHANGE
  - на REVISE/FINAL изменён стиль или bpm без GAP/FAIL причины

---

## [M] GATES
PASS если:
- step_id корректен и соблюдены locks
- есть result_summary + scorecard
- есть next_action
- нет символа `!` во всех текстах

FAIL если:
- любое FAIL condition

---

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [QA]
- Handoff to:
  - MUS.HOOK_FOCUS_LOOP
  - MUS.MIX_FOCUS_LOOP
  - MUS.LYRICS_FOCUS_LOOP
  - MUS.QA_CHECKS
  - MUS.RELEASE_ASSEMBLER

---

## [M] CHANGELOG
- 2026-02-02: v1.0.0 init
- 2026-02-04: v1.1.0 deterministic locks, mode behavior, scorecard, routing triggers
