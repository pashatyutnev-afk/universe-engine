FILE: UE_V2/03_ENT/50_VAL_ENT/20_VIDEO_VAL_ENT/90__VID__NEGATIVE_SPEC__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 20_VIDEO_VAL_ENT
DOC_TYPE: VAL_ENTITY
DOMAIN: VID_VAL_ENT
UID: UE.V2.ENT.VAL.VID.NEGATIVE_SPEC.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: VID_NEGATIVE_SPEC_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.VID.NEGATIVE_SPEC.001

## [M] PURPOSE
Валидирует наличие и достаточность negative constraints для видео-промпта:
- качество/артефакты,
- запрет watermark/text overlays,
- subject lock (если заявлен),
- стабильность камеры (если не запрошено иначе),
- корректность параметров экспорта (если заявлены).

## [M] SCOPE
- TARGET_DOMAIN: VID
- APPLIES_TO: [PROMPT_PACK, NEGATIVE_PROMPT, SHOT_PLAN?, EXPORT_HINTS?, VID_BRIEF?]
- NON_GOALS: [выбор стиля вместо brief, монтажные решения, конкретные цветовые палитры]

## [M] INPUTS / OUTPUTS
- Inputs:
  - VID_BRIEF?: цель, длительность, subject lock, стиль-свитчи, разрешение
  - PROMPT_PACK?: MAIN_PROMPT + NEGATIVE_PROMPT + PARAMS?
  - SHOT_PLAN?: таймлайн/биты, если есть свитчи стиля
  - EXPORT_HINTS?: fps/aspect/duration, если есть
- Outputs:
  - VAL_DECISION: PASS|FAIL|WARN|ASK
  - VAL_FINDINGS: [short findings]
  - REQUIRED_FIXES: [minimal fixes]
  - VIOLATIONS: [violation ids]
  - FAIL_CODE?: UE.FAIL.INPUT_ABSENT|UE.FAIL.GATE_FAIL|UE.FAIL.RULE_VIOLATION

## [M] CHECKS
- C1: NEGATIVE_PROMPT присутствует. (Evidence: PROMPT_PACK contains NEGATIVE_PROMPT)
- C2: NEGATIVE_PROMPT содержит core запреты:
  - no watermarks/logos/text overlays,
  - avoid blur/noise/compression artifacts,
  - avoid extra people/objects not in brief.
  (Evidence: key phrases or equivalent)
- C3: Если VID_BRIEF требует single subject lock:
  - NEGATIVE_PROMPT запрещает identity drift / face change / hair length change,
  - нет разрешения на “replace subject”.
  (Evidence: subject-lock block present)
- C4: Если заявлены style switches:
  - есть SHOT_PLAN или эквивалент timeline.
  (Evidence: shot plan)
- C5: Если заявлены export параметры:
  - duration/aspect/resolution не конфликтуют внутри пакета.
  (Evidence: export hints consistency)

## [M] EVIDENCE_REQUIREMENTS
- E1: PASS возможен только если NEGATIVE_PROMPT явно присутствует.
- E2: Если нет PROMPT_PACK -> ASK, а не PASS.
- E3: Если subject lock обязателен и нет защитного блока -> WARN (или FAIL, если это обязательный hard constraint).
- E4: Если style switches > 0 и нет timeline -> ASK.

## [M] DECISION_MATRIX
- IF PROMPT_PACK отсутствует -> ASK (VIOLATIONS: V.VID.NEG.NO_PACK)
- IF NEGATIVE_PROMPT отсутствует -> FAIL (UE.FAIL.GATE_FAIL; V.VID.NEG.MISSING)
- IF missing core запретов -> WARN (V.VID.NEG.CORE_INCOMPLETE)
- IF subject lock обязателен и нет guard -> WARN (V.VID.SUBJECT.LOCK_MISSING)
- IF style switches заявлены и нет timeline -> ASK (V.VID.STYLE.NO_TIMELINE)
- IF export hints конфликтуют -> FAIL (UE.FAIL.GATE_FAIL; V.VID.EXPORT.CONFLICT)
- ELSE -> PASS

## [M] VIOLATIONS
- V.VID.NEG.NO_PACK — нет PROMPT_PACK
- V.VID.NEG.MISSING — нет NEGATIVE_PROMPT
- V.VID.NEG.CORE_INCOMPLETE — core блок неполный
- V.VID.SUBJECT.LOCK_MISSING — нет защиты subject lock
- V.VID.STYLE.NO_TIMELINE — нет таймлайна при сменах стиля
- V.VID.EXPORT.CONFLICT — конфликт параметров экспорта

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION

## [M] KB SCOPE
- KB Inputs: [brief, prompt pack, shot plan, export hints]
- KB Outputs: [validation findings + required fixes]
- KB Boundaries: [не добавлять новые объекты/стиль; не делать внешние ссылки; не “угадывать” intent]
- KB RAW refs: []

## [M] GATES
- PASS if:
  - NEGATIVE_PROMPT есть
  - core запреты присутствуют
  - subject lock защищён, если обязателен
  - при style switches есть timeline
  - export параметры не конфликтуют, если заданы
- FAIL if:
  - NEGATIVE_PROMPT отсутствует
  - export конфликт подтверждён

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT, QA_ENT]
- Handoff rules:
  - ASK -> запросить минимальный вход (PROMPT_PACK / SHOT_PLAN)
  - WARN -> вернуть REQUIRED_FIXES (добавить missing blocks)
  - FAIL -> стоп до исправления
