FILE: UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/06__MUS__FINGERPRINT_COLLISION_THRESHOLDS__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 10_MUSIC_CONTROLLERS_CTL_ENT
DOC_TYPE: CTL_BLOCKER
DOMAIN: MUS_CTL_ENT
UID: UE.V2.ENT.CTL.MUS.FINGERPRINT_COLLISION_THRESHOLDS.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] BLOCKER_HEADER
- BLOCKER_NAME: MUS_FINGERPRINT_COLLISION_THRESHOLDS
- BLOCKER_CLASS: CTL_BLOCKER
- UID: UE.V2.ENT.CTL.MUS.FINGERPRINT_COLLISION_THRESHOLDS.001
- SEVERITY: BLOCK
- DEFAULT_ACTION: ASK
- STATUS: ACTIVE

## [M] PURPOSE
Политика порогов коллизий. Блокирует релиз при признаках высокой похожести или пересечения с внутренним каталогом.

## [M] TRIGGERS
- T1: Нет данных о сравнении с внутренним каталогом, а релиз заявлен как готовый.
- T2: Обнаружена высокая похожесть по ключевому мотиву/хуку (по заметкам/проверке).
- T3: Повторение уникальной фразы/хук-фразы из уже выпущенного трека.

## [M] REQUIRED_FIXES
- Fix1: Дать notes сравнения с каталогом (что отличается).
- Fix2: Изменить хук, мелодический контур или ритм-характер.
- Fix3: Обновить текст припева и ключевые фразы.

## [M] OVERRIDE_POLICY
- OVERRIDE_ALLOWED: true
- OVERRIDE_REQUIREMENTS:
  - требуется явное подтверждение владельца каталога в внешнем контуре
  - требуется описание отличий как факты
- OVERRIDE_LOGGING:
  - сохранить token-only: collision notes, decision token

## [M] VIOLATIONS
- V.COL.NO_CHECK
- V.COL.HIGH_SIMILARITY
- V.COL.CATALOG_REPEAT

## [M] FAIL_CODES
- UE.FAIL.APPROVAL_REQUIRED
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [catalog memory token, variant notes]
- KB Outputs: [block or ask decision]
- KB Boundaries: [не “угадывать” что коллизии нет]
- KB RAW refs: []

## [M] GATES
- PASS if: есть доказуемые отличия или проверка не выявила коллизию
- FAIL if: коллизия подтверждена и не исправлена

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, QA_ENT, VAL_ENT]
- Handoff rules: ASK -> require collision notes; FAIL -> stop
