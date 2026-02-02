FILE: UE_V2/03_ENT/40_CTL_ENT/20_VIDEO_CONTROLLERS_CTL_ENT/90__VID__NEGATIVE_SPEC_LIBRARY__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 20_VIDEO_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: VID_CTL_ENT
UID: UE.V2.ENT.CTL.VID.NEGATIVE_SPEC_LIBRARY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: VID_NEGATIVE_SPEC_LIBRARY_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.VID.NEGATIVE_SPEC_LIBRARY.001

## [M] PURPOSE
Единая библиотека negative constraints для видео: помогает удерживать subject lock, избегать артефактов и конфликтов стиля.
Использовать как готовые блоки NEGATIVE_PROMPT и запреты параметров.

## [M] SCOPE
- TARGET_DOMAIN: VID
- APPLIES_TO: [PROMPT_PACK, NEGATIVE_PROMPT, PARAMS, EXPORT_HANDOFF_TOKEN]
- NON_GOALS: [выбор стиля, монтажные решения, конкретные палитры]

## [M] INPUTS / OUTPUTS
- Inputs:
  - VID_BRIEF?: цель, длительность, subject lock, разрешение
  - SHOT_PLAN?: тайминг и биты
  - PROMPT_PACK?: основной промпт и параметры
- Outputs:
  - CTL_DECISION: PASS|WARN|ASK|FAIL
  - CTL_FINDINGS: [findings]
  - REQUIRED_FIXES: [fixes]
  - FAIL_CODE?: UE.FAIL.RULE_VIOLATION|UE.FAIL.INPUT_ABSENT

## [M] RULESET (library blocks)

### [L] NEGATIVE_CORE (always-on)
- Avoid: low quality, blurry, noisy, compression artifacts, banding, flicker, frame jitter, ghosting, warped anatomy, extra limbs, melted faces, broken hands.
- Avoid: text overlays, watermarks, logos, subtitles, UI elements, timestamps.
- Avoid: sudden scene changes, random cuts, jump discontinuities.
- Avoid: duplicate subjects, extra people, unexpected props.

### [L] SUBJECT_LOCK_GUARD
- If subject is a single person: avoid face change, avoid identity drift, avoid hair length/skin tone changes, avoid outfit drift unless explicitly planned.
- If subject must stay constant: avoid replacing subject with another person, avoid age change.

### [L] CAMERA_STABILITY_GUARD
- Avoid: camera shake unless requested.
- Avoid: aggressive zooms, whip pans, random reframe.
- Avoid: inconsistent focal length across beats without plan.

### [L] STYLE_SWITCH_GUARD (for multi-style videos)
- Avoid: style mixing within a single beat unless planned.
- Avoid: uncontrolled morphing that breaks subject identity.
- Require: style timeline in SHOT_PLAN when switches > 0.

### [L] EXPORT_GUARD
- Require: output resolution and duration match brief.
- Avoid: variable frame rate if platform expects constant.
- Avoid: mismatched aspect ratio.

## [M] DECISION_MATRIX
- IF PROMPT_PACK отсутствует -> ASK (дать PROMPT_PACK)
- IF нет NEGATIVE_PROMPT -> WARN (добавить NEGATIVE_CORE)
- IF subject lock требование есть, но промпт допускает drift -> WARN (добавить SUBJECT_LOCK_GUARD)
- IF стиль-свитчи заявлены, но нет timeline -> ASK
- ELSE -> PASS

## [M] VIOLATIONS
- V.VID.NEG.MISSING — отсутствует negative prompt
- V.VID.SUBJECT.DRIFT_RISK — риск дрейфа личности/объекта
- V.VID.STYLE.NO_TIMELINE — нет таймлайна стилей при свитчах
- V.VID.EXPORT.MISMATCH — параметры экспорта не совпадают с brief

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION

## [M] KB SCOPE
- KB Inputs: [brief/shot plan/prompt pack/export settings]
- KB Outputs: [negative blocks + fixes]
- KB Boundaries: [не добавлять новые объекты, не придумывать стиль вне brief]
- KB RAW refs: []

## [M] GATES
- PASS if:
  - negative core присутствует
  - subject lock защищён, если нужен
  - экспортные параметры не конфликтуют
- FAIL if:
  - заявлены обязательные свитчи стиля, но нет таймлайна и нельзя продолжать без входа

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT, VAL_ENT]
- Handoff rules:
  - WARN -> patch prompt pack and continue
  - ASK -> request minimal missing inputs
  - FAIL -> stop and return REQUIRED_FIXES
