# GLOSSARY (TERMS) (CANON)
FILE: 02_STANDARDS/04_TERMS_DEFINITIONS/GLOSSARY.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: TERMS
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.TERMS.GLOSSARY.400
OWNER: SYSTEM
ROLE: Canonical glossary for Universe Engine terminology. Source-of-Truth for controlled terms used across SYSTEM_LAW, STANDARDS, and KB governance.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован глоссарий: единый формат терминов, правила употребления, UID-first XREF на SoT документы"
- REASON: "Убрать разночтения терминов между слоями"
- IMPACT: "All docs and registries"

---

## XREF (UID-first)
XREF: UE.STD.SPEC.DOC_CONTROL.103 | depends_on | doc header standard | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | linking standard | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md
XREF: UE.STD.SPEC.UID_MARKING.101 | references | UID/marking terminology | 02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md
XREF: UE.STD.SPEC.STORAGE_MAP.102 | references | layer/storage terminology | 02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md

---

## 0) PURPOSE (LAW)
Этот глоссарий — единая точка истины по терминологии Universe Engine.
Если термин определён здесь, он используется единообразно во всех слоях.

### TERM RULE (ABSOLUTE)
- Если термин используется в каноне — он должен быть определён здесь (или явной ссылкой на источник определения).
- Если термин не определён — он считается “невалидным/размытым” и должен быть либо добавлен, либо заменён на существующий.

---

## 1) TERM RECORD FORMAT (STANDARD)
Каждый термин оформляется так:

- TERM: `<Name>`
- KEY: `<STABLE_KEY>`
- DEFINITION: `<one paragraph>`
- USAGE: `<rules / constraints>`
- XREF (optional): `XREF: <UID> | references | <why> | <path(optional)>`

---

## 2) CONTROLLED TERMS (SoT)

### ARTIFACT
- TERM: Artifact
- KEY: ARTIFACT
- DEFINITION: Любой объект системы, который является результатом работы (документ, паспорт, сцена, профиль, и т.д.) и может иметь UID.
- USAGE: Используй как общий термин. Уточняй через `ARTIFACT_TYPE` если нужно.
- XREF: XREF: UE.STD.SPEC.DOC_CONTROL.103 | references | artifact header usage | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

### CANON
- TERM: Canon
- KEY: CANON
- DEFINITION: Совокупность материалов, признанных системой истинными и обязательными к применению.
- USAGE: Канон определяется мастер-индексами слоёв. Всё вне индексов — non-canon.

### CANON PROTOCOL
- TERM: Canon Protocol
- KEY: CANON_PROTOCOL
- DEFINITION: Процедура изменения канона (как меняются законы/спеки/индексы).
- USAGE: Любые правки индексов/SoT контрактов проходят Canon Protocol.
- XREF: XREF: UE.LAW.CANON.PROTOCOL.004 | references | canon change flow | 01_SYSTEM_LAW/04__CANON_PROTOCOL.md

### CHANGE NOTE
- TERM: Change Note
- KEY: CHANGE_NOTE
- DEFINITION: Блок фиксации последнего изменения документа (дата/тип/summary/reason/impact).
- USAGE: Обязателен в Doc Control header для канона.
- XREF: XREF: UE.STD.SPEC.DOC_CONTROL.103 | references | header format | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

### COMPLIANCE
- TERM: Compliance
- KEY: COMPLIANCE
- DEFINITION: Состояние соответствия документа требованиям системы (header/UID/SemVer/naming/constraints).
- USAGE: Используется в реестрах (OK/PENDING/INVALID).
- XREF: XREF: UE.STD.SPEC.DOC_REGISTRY.107 | references | compliance enum | 02_STANDARDS/01_SPECIFICATIONS/07__DOC_REGISTRY_STANDARD.md

### DEPRECATED
- TERM: Deprecated
- KEY: DEPRECATED
- DEFINITION: Статус документа/объекта, который считается устаревшим и заменённым новым.
- USAGE: Deprecated документ сохраняется для истории и миграции, но не является рекомендуемым для применения. Обязан иметь `DEPRECATED_BY`.
- XREF: XREF: UE.STD.SPEC.DOC_CONTROL.103 | references | deprecation rules | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

### DOC CONTROL HEADER
- TERM: Doc Control Header
- KEY: DOC_CONTROL_HEADER
- DEFINITION: Стандартизированная шапка документа, содержащая FILE/LAYER/DOC_TYPE/UID/VERSION/LOCK/STATUS и т.д.
- USAGE: Обязателен для любого канонического документа.
- XREF: XREF: UE.STD.SPEC.DOC_CONTROL.103 | defines | header contract | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

### DOC REGISTRY
- TERM: Doc Registry
- KEY: DOC_REGISTRY
- DEFINITION: Реестр документов слоя, инвентаризация состава и контроль качества (compliance).
- USAGE: Не определяет существование (existence задаёт master-index), а контролирует качество.
- XREF: XREF: UE.STD.SPEC.DOC_REGISTRY.107 | defines | registry rules | 02_STANDARDS/01_SPECIFICATIONS/07__DOC_REGISTRY_STANDARD.md

### DOC TYPE
- TERM: Doc Type
- KEY: DOC_TYPE
- DEFINITION: Контролируемый тип документа (SPEC/MODULE/PROTOCOL/TEMPLATE/INDEX/REGISTRY/TERMS...).
- USAGE: Всегда указывается в header как `DOC_TYPE`.

### ENTRYPOINT
- TERM: Entrypoint
- KEY: ENTRYPOINT
- DEFINITION: Единая точка входа в область (слой/realm), обычно master-index.
- USAGE: У каждой области один entrypoint. Альтернативные entrypoints не канон.
- XREF: XREF: UE.STD.SPEC.STORAGE_MAP.102 | references | entrypoint rule | 02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md

### EXISTENCE RULE
- TERM: Existence Rule
- KEY: EXISTENCE_RULE
- DEFINITION: Закон “существует только то, что зарегистрировано в индексе”.
- USAGE: Применяется в master-index и под-индексах как абсолютное правило.

### INDEX
- TERM: Index
- KEY: INDEX
- DEFINITION: Навигационный документ, определяющий состав и порядок объектов (и их существование в области).
- USAGE: Master-index — главный для слоя. Под-индекс — для подпапки/реалма.
- XREF: XREF: UE.STD.TPL.INDEX_TEMPLATE.301 | references | index format | 02_STANDARDS/03_TECHNICAL/INDEX_TEMPLATE.md

### LAYER
- TERM: Layer
- KEY: LAYER
- DEFINITION: Структурный уровень системы (папка верхнего уровня), имеющий собственный master-index и правила.
- USAGE: Всегда указывается в header как `LAYER: <...>`.

### LEGACY ALIAS (NON-CANON)
- TERM: Legacy Alias (Non-Canon)
- KEY: LEGACY_ALIAS
- DEFINITION: Файл-указатель на канонический документ, оставленный для совместимости/старых ссылок.
- USAGE: Не содержит контента стандарта. Содержит только `CANON_TARGET` и пометку DEPRECATED.

### LOCK
- TERM: Lock
- KEY: LOCK
- DEFINITION: Поле управления изменяемостью документа (`FIXED` или `OPEN`).
- USAGE: `FIXED` = канон, правки только через Canon Protocol. `OPEN` = черновик.
- XREF: XREF: UE.STD.SPEC.DOC_CONTROL.103 | references | lock meanings | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

### MASTER-INDEX
- TERM: Master-Index
- KEY: MASTER_INDEX
- DEFINITION: Главный индекс слоя (entrypoint), определяющий существование объектов слоя.
- USAGE: В одном слое ровно один master-index. Всё остальное — sub-index или non-canon.

### MODULE
- TERM: Module
- KEY: MODULE
- DEFINITION: Документ детализации, расширяющий SoT-спеку, но не являющийся источником истины.
- USAGE: Module обязан ссылаться на SoT через `extends` и не должен дублировать SoT.
- XREF: XREF: UE.STD.SPEC.UID_MARKING.101 | references | SoT vs Modules boundary | 02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md

### REALM
- TERM: Realm
- KEY: REALM
- DEFINITION: Доменная область знаний/контента (особенно в KB): Narrative/Character/Visual/Sound/Production/Marketing/etc.
- USAGE: Realm управляется governance и имеет собственную структуру/правила.

### REGISTRY
- TERM: Registry
- KEY: REGISTRY
- DEFINITION: Реестр объектов/схем/пайплайнов/доков (табличный контроль состава и параметров).
- USAGE: Registry не обязательно задаёт existence, если не является индексом.

### REL / XREF
- TERM: REL / XREF
- KEY: REL_XREF
- DEFINITION: Политика связей и cross-reference между объектами системы в формате UID-first.
- USAGE: Внутренние ссылки всегда содержат UID. Тип связи берётся из controlled enum.
- XREF: XREF: UE.STD.SPEC.REL_XREF.104 | defines | xref format and rel types | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

### SCENE PACK
- TERM: Scene Pack
- KEY: SCENE_PACK
- DEFINITION: Документ-контейнер сцены, содержащий метаданные и 4 канонических трека.
- USAGE: Должен соответствовать 4Track SoT (4 трека всегда присутствуют).
- XREF: XREF: UE.STD.SPEC.SCENE_4TRACK.105 | references | scene pack contract | 02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md

### SEMVER
- TERM: SemVer
- KEY: SEMVER
- DEFINITION: Семантическая версия `MAJOR.MINOR.PATCH`, отражающая характер изменений.
- USAGE: Контрактные изменения = MAJOR. Добавления без breaking = MINOR. Исправления = PATCH.
- XREF: XREF: UE.LAW.VERSIONING.003 | references | versioning policy | 01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md

### SoT (SOURCE OF TRUTH)
- TERM: SoT (Source of Truth)
- KEY: SOT
- DEFINITION: Единственный документ/спека, который является первичной истиной по смыслу.
- USAGE: Один смысл → один SoT. Всё остальное — references/modules/templates.

### STATUS
- TERM: Status
- KEY: STATUS
- DEFINITION: Поле состояния документа (ACTIVE/DEPRECATED/ARCHIVED/DRAFT).
- USAGE: Это статус документа, не путать со статусом сущности мира.

### STORAGE MAP
- TERM: Storage Map
- KEY: STORAGE_MAP
- DEFINITION: Правила размещения слоёв/папок/entrypoints и “где что живёт”.
- USAGE: Любое отклонение — через Canon Protocol.
- XREF: XREF: UE.STD.SPEC.STORAGE_MAP.102 | defines | placement rules | 02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md

### TEMPLATE
- TERM: Template
- KEY: TEMPLATE
- DEFINITION: Шаблон документа/артефакта (копируемая форма), реализующий контракт SoT.
- USAGE: Template может расширять поля, но не может менять обязательный контракт.

### TRACK EVENT
- TERM: Track Event
- KEY: TRACK_EVENT
- DEFINITION: Атомарное событие на одном из 4 треков сцены (имеет EVENT_TRACK и ORDER).
- USAGE: Используется в Scene Stack 4Track. Может храниться отдельно от Scene Pack.
- XREF: XREF: UE.STD.SPEC.SCENE_4TRACK.105 | references | event contract | 02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md

### UID
- TERM: UID
- KEY: UID
- DEFINITION: Уникальный неизменяемый идентификатор в системе, первичный ключ для ссылок.
- USAGE: UID-first везде. UID нельзя менять без Canon Protocol.
- XREF: XREF: UE.LAW.UID.002 | references | UID rules | 01_SYSTEM_LAW/02__UID_RULES.md

---

## 3) ADDING NEW TERMS (RULE)
Если нужно добавить термин:
1) Добавь запись по формату Term Record.
2) Если термин привязан к документу-источнику — добавь XREF на UID.
3) Если термин вводит новый controlled enum/контракт — это изменение канона и проходит Canon Protocol.

---

## FINAL RULE (LOCK)
Этот глоссарий — SoT терминов Universe Engine.
Любая правка терминов, влияющая на смысл контрактов/enum = изменение канона.
--- END.
