# STATUS / LOCK / VERSION (MARKING MODULE) (CANON)
FILE: 02_STANDARDS/06_MARKING_STANDARDS/03__STATUS_LOCK_VERSION.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: MODULE
MODULE_TYPE: MARKING
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.MOD.MARKING.STATUS_LOCK_VERSION.603
OWNER: SYSTEM
ROLE: Marking module detailing how to mark STATUS, LOCK, and VERSION fields across documents and artifacts, including deprecation markers and the separation between doc-status and entity-status.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Модуль Status/Lock/Version: doc-status vs entity-status, semver bump guidance, deprecation markers, lock rules"
- REASON: "Убрать путаницу статусов и сделать единый способ маркировки изменений"
- IMPACT: "All canon docs and artifacts"

---

## XREF (UID-first)
XREF: UE.STD.SPEC.DOC_CONTROL.103 | extends | this module details status/lock usage | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
XREF: UE.LAW.VERSIONING.003 | depends_on | SemVer change policy | 01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | deprecation linking rules | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

## 0) PURPOSE
Этот модуль фиксирует:
- как корректно использовать `STATUS` и `LOCK` в Doc Control header
- как разделять “статус документа” и “статус сущности/объекта”
- как маркировать SemVer `VERSION`
- как оформлять DEPRECATED/ARCHIVED без ломания канона

---

## 1) DOC STATUS (DOCUMENT LIFECYCLE)
### 1.1 STATUS refers to DOCUMENT only (ABSOLUTE)
`STATUS` в header всегда означает состояние **документа**, а не сущности.

Allowed (controlled):
- `ACTIVE`
- `DEPRECATED`
- `ARCHIVED`
- `DRAFT` (не канон)

### 1.2 DRAFT rule
- `STATUS: DRAFT` ⇒ документ не должен быть зарегистрирован в master-index канона.

---

## 2) ENTITY STATUS (SEPARATE FIELD)
Если нужно состояние сущности мира/объекта:
- используй отдельное поле внутри содержимого:
  - `ENTITY_STATUS: <draft|active|retired|dead|lost|...>` (свободная строка)
или аналогичное:
- `SCENE_STATUS`
- `CHARACTER_STATUS`
- `ASSET_STATUS`

Запрещено:
- использовать header `STATUS` для описания сущности.

---

## 3) LOCK MEANING (EDITABILITY)
### 3.1 LOCK applies to doc governance
- `LOCK: FIXED` — каноничный документ. Правки только через Canon Protocol.
- `LOCK: OPEN` — черновик/рабочий.

### 3.2 FIXED implies index registration (expected)
Для L1 документов канона:
- `LOCK: FIXED` обычно означает: документ зарегистрирован в master-index.

Исключение:
- alias pointers (legacy) могут быть FIXED, даже если не “контент”, но они регистрируются как legacy/dep.

---

## 4) VERSION (SEMVER) MARKING
### 4.1 VERSION always SemVer
Формат:
- `MAJOR.MINOR.PATCH`

### 4.2 SemVer bump guidance (practical)
- PATCH: правки текста/ссылок/опечаток, не меняющие контракт
- MINOR: добавление новых правил/полей “по желанию”, без breaking
- MAJOR: изменение обязательных полей/enum/контрактов/структуры

### 4.3 Version stability rule
`VERSION` в header всегда отражает версию документа как артефакта канона.

---

## 5) DEPRECATION MARKERS (REQUIRED)
Если документ устаревает:
- `STATUS: DEPRECATED`
- `DEPRECATED_BY: <UID_NEW>`
- XREF: `deprecated_by` на новый UID

Рекомендация:
- в начале содержания секция “DEPRECATION NOTICE”:
  - почему устарел
  - куда мигрировать (UID + PATH)

---

## 6) ARCHIVE MARKERS
Если документ уходит в историю (архив):
- `STATUS: ARCHIVED`
- (опционально) `ARCHIVE_REASON: "<...>"` внутри текста

Важно:
- ARCHIVED не должен быть “ссылкой на новый” — это роль DEPRECATED.

---

## 7) CHANGE NOTE RULES
Change Note — обязателен в канонических документах и фиксирует **последнее изменение**:
- DATE
- TYPE (PATCH/MINOR/MAJOR)
- SUMMARY/REASON/IMPACT

Не делать “многострочный роман” — только суть.

---

## 8) MIGRATION NOTES
S0:
- во всех паспортах/реалмах заменить неправильное использование `STATUS` (где им описывали сущности)
- привести deprecation к `DEPRECATED_BY + XREF deprecated_by`
- привести VERSION к SemVer

---

## FINAL RULE (LOCK)
Этот модуль расширяет Doc Control + Versioning policy и обязателен для маркировки жизненного цикла.
Любая правка controlled enum или смысла STATUS/LOCK/VERSION = MAJOR по умолчанию.
--- END.
