# DOC REGISTRY — STANDARDS LAYER (CANON)
FILE: 02_STANDARDS/01__DOC_REGISTRY.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.REG.STD.DOC.MASTER.001
OWNER: SYSTEM
ROLE: Canonical registry of all documents inside 02_STANDARDS. Defines document inventory, type classification, and compliance state (Doc Control/UID/SemVer/Naming).

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MAJOR
- SUMMARY: "Создан канонический реестр документов 02_STANDARDS (UID-first) и начата миграция именования/DocControl"
- REASON: "Ранее реестр существовал в конфликтующем имени 00__* и не мог быть каноном"
- IMPACT: "Навигация и контроль состава STANDARDS"

---

## 0) PURPOSE (LAW)
Этот реестр — единая точка истины о составе документов слоя `02_STANDARDS`.

Он фиксирует:
- полный список файлов STANDARDS
- тип документа (SPEC/MODULE/PROTOCOL/TEMPLATE/TERMS/INDEX/REGISTRY)
- приоритет/роль
- состояние соответствия законам системы (UID/Naming/DocControl/SemVer)

### EXISTENCE RULE (ABSOLUTE)
Если файла нет в master-index слоя `02_STANDARDS/00__INDEX__STANDARDS.md` — он не существует для слоя STANDARDS.
Этот реестр — инвентаризация и контроль качества состава.

---

## 1) HOW TO USE (MANDATORY FLOW)
1) Открываешь `02_STANDARDS/00__INDEX__STANDARDS.md` (entrypoint).
2) Находишь документ по категории (SPEC/MODULE/PROTOCOL/...).
3) Проверяешь здесь:
   - DOC_UID (какой UID должен быть в шапке файла)
   - COMPLIANCE (OK/PENDING)
4) Если COMPLIANCE = PENDING — документ канонически зарегистрирован, но требует нормализации по законам (см. Migration Plan).

---

## 2) DOC TYPES (CONTROLLED ENUM)
- INDEX — master-index слоя/подслоя
- REGISTRY — реестр (таблица состава/типов/схем)
- SPEC — SoT specification (главная спека)
- MODULE — модуль детализации (НЕ SoT)
- PROTOCOL — операционная процедура
- TEMPLATE — шаблон/форма
- TERMS — глоссарий/термины
- REQUIREMENTS — требования/ТЗ индекс

---

## 3) REGISTRY TABLE — 02_STANDARDS INVENTORY

Legend:
- COMPLIANCE: OK | PENDING
- TARGET_VERSION: версия, к которой приводим документ при нормализации

### A) Layer entrypoints / root
| DOC_UID | DOC_TYPE | TITLE | STATUS | LOCK | COMPLIANCE | TARGET_VERSION | PATH |
|---|---|---|---|---|---|---|---|
| UE.IDX.STD.MASTER.000 | INDEX | STANDARDS INDEX (Master) | ACTIVE | FIXED | OK | 1.1.0 | 02_STANDARDS/00__INDEX__STANDARDS.md |
| UE.REG.STD.DOC.MASTER.001 | REGISTRY | DOC REGISTRY (This file) | ACTIVE | FIXED | OK | 1.0.0 | 02_STANDARDS/01__DOC_REGISTRY.md |
| UE.IDX.STD.MASTER_MAP.002 | INDEX | MASTER INDEX — UNIVERSE ENGINE (Standards layer view) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/02__MASTER_INDEX__UNIVERSE_ENGINE.md |

NOTE:
- `02__MASTER_INDEX__UNIVERSE_ENGINE.md` создаётся переименованием из `00__MASTER_INDEX__UNIVERSE_ENGINE.md` (см. Migration Plan).

---

### B) 00_CANON
| DOC_UID | DOC_TYPE | TITLE | STATUS | LOCK | COMPLIANCE | TARGET_VERSION | PATH |
|---|---|---|---|---|---|---|---|
| UE.STD.CANON.ARCH_OVERVIEW.010 | SPEC | Architecture Overview | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/00_CANON/ARCHITECTURE_OVERVIEW.md |
| UE.STD.CANON.SYSTEM_CANON.011 | SPEC | System Canon (Standards) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/00_CANON/SYSTEM_CANON.md |

---

### C) 01_SPECIFICATIONS (SoT)
| DOC_UID | DOC_TYPE | TITLE | STATUS | LOCK | COMPLIANCE | TARGET_VERSION | PATH |
|---|---|---|---|---|---|---|---|
| UE.STD.SPEC.UID_MARKING.101 | SPEC | UID & Marking Standard (SoT) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md |
| UE.STD.SPEC.STORAGE_MAP.102 | SPEC | Storage Map Standard (SoT) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md |
| UE.STD.SPEC.DOC_CONTROL.103 | SPEC | Doc Control Standard (SoT) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md |
| UE.STD.SPEC.REL_XREF.104 | SPEC | REL Policy + XREF Standard (SoT) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md |
| UE.STD.SPEC.SCENE_4TRACK.105 | SPEC | Scene Stack 4Track Standard (SoT) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md |
| UE.STD.TPL.SCENE_PACK.105A | TEMPLATE | Template: Scene Pack | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/01_SPECIFICATIONS/05A__TEMPLATE__SCENE_PACK.md |
| UE.STD.TPL.TRACK_EVENT.105B | TEMPLATE | Template: Track Event | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/01_SPECIFICATIONS/05B__TEMPLATE__TRACK_EVENT.md |
| UE.STD.SPEC.NAT_GATES.106 | SPEC | Naturalness Gates Standard (SoT) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/01_SPECIFICATIONS/06__NATURALNESS_GATES_STANDARD.md |
| UE.STD.TPL.NAT_PROFILE.106A | TEMPLATE | Template: NAT Profile | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/01_SPECIFICATIONS/06A__TEMPLATE__NAT_PROFILE.md |
| UE.STD.SPEC.DOC_REGISTRY.107 | SPEC | Doc Registry Standard (SoT) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/01_SPECIFICATIONS/07__DOC_REGISTRY_STANDARD.md |

LEGACY / TO-NORMALIZE (currently non-SoT until normalized):
| DOC_UID | DOC_TYPE | TITLE | STATUS | LOCK | COMPLIANCE | TARGET_VERSION | PATH |
|---|---|---|---|---|---|---|---|
| UE.STD.LEGACY.ENTITY_MODEL.190 | SPEC | Entity Model Spec (legacy) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/01_SPECIFICATIONS/ENTITY_MODEL_SPEC.md |
| UE.STD.LEGACY.INDEX_STRUCTURE.191 | SPEC | Index Structure Spec (legacy) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/01_SPECIFICATIONS/INDEX_STRUCTURE_SPEC.md |

---

### D) 02_PROTOCOLS
| DOC_UID | DOC_TYPE | TITLE | STATUS | LOCK | COMPLIANCE | TARGET_VERSION | PATH |
|---|---|---|---|---|---|---|---|
| UE.STD.PROTOCOL.CHANGE_MGMT.200 | PROTOCOL | Change Management Protocol | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/02_PROTOCOLS/CHANGE_MANAGEMENT_PROTOCOL.md |
| UE.STD.PROTOCOL.CHAT.201 | PROTOCOL | Chat Protocol | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/02_PROTOCOLS/CHAT_PROTOCOL.md |

---

### E) 03_TECHNICAL
| DOC_UID | DOC_TYPE | TITLE | STATUS | LOCK | COMPLIANCE | TARGET_VERSION | PATH |
|---|---|---|---|---|---|---|---|
| UE.STD.TPL.ENTITY_PASSPORT.300 | TEMPLATE | Entity Passport Template | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/03_TECHNICAL/ENTITY_PASSPORT_TEMPLATE.md |
| UE.STD.TPL.INDEX_TEMPLATE.301 | TEMPLATE | Index Template | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/03_TECHNICAL/INDEX_TEMPLATE.md |

---

### F) 04_TERMS_DEFINITIONS
| DOC_UID | DOC_TYPE | TITLE | STATUS | LOCK | COMPLIANCE | TARGET_VERSION | PATH |
|---|---|---|---|---|---|---|---|
| UE.STD.TERMS.GLOSSARY.400 | TERMS | Glossary | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/04_TERMS_DEFINITIONS/GLOSSARY.md |

---

### G) 05_REQUIREMENTS_TZ
| DOC_UID | DOC_TYPE | TITLE | STATUS | LOCK | COMPLIANCE | TARGET_VERSION | PATH |
|---|---|---|---|---|---|---|---|
| UE.STD.REQ.INDEX.500 | REQUIREMENTS | Requirements Index | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/05_REQUIREMENTS_TZ/00__INDEX.md |

---

### H) 06_MARKING_STANDARDS (Modules)
Rule: Modules are NOT SoT. They must extend the SoT specs and reference them.

| DOC_UID | DOC_TYPE | TITLE | STATUS | LOCK | COMPLIANCE | TARGET_VERSION | PATH |
|---|---|---|---|---|---|---|---|
| UE.STD.MODULE.ID_STANDARD.601 | MODULE | ID Standard (Module) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/06_MARKING_STANDARDS/01__ID_STANDARD.md |
| UE.STD.MODULE.STORAGE_MAP.602 | MODULE | Storage Map (Module) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/06_MARKING_STANDARDS/02__STORAGE_MAP.md |
| UE.STD.MODULE.STATUS_LOCK_VERSION.603 | MODULE | Status / Lock / Version (Module) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/06_MARKING_STANDARDS/03__STATUS_LOCK_VERSION.md |
| UE.STD.MODULE.PRIORITY.604 | MODULE | Priority S0–S3 (Module) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/06_MARKING_STANDARDS/04__PRIORITY_S0_S3.md |
| UE.STD.MODULE.REL_XREF.605 | MODULE | REL Policy + XREF (Module) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/06_MARKING_STANDARDS/05__REL_POLICY_XREF.md |
| UE.STD.MODULE.SCENE_4TRACK.606 | MODULE | Scene Stack 4Track (Module) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/06_MARKING_STANDARDS/06__SCENE_STACK_4TRACK.md |
| UE.STD.MODULE.NAT_GATES.607 | MODULE | Naturalness Gates (Module) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/06_MARKING_STANDARDS/07__NATURALNESS_GATES.md |
| UE.STD.MODULE.DOC_CONTROL.608 | MODULE | Doc Control (Module) | ACTIVE | FIXED | PENDING | 1.0.0 | 02_STANDARDS/06_MARKING_STANDARDS/08__DOC_CONTROL.md |

---

## 4) COMPLIANCE RULES (WHAT “OK” MEANS)
COMPLIANCE = OK только если документ:
- имеет полный Doc Control header
- имеет UID (совпадающий с DOC_UID из этого реестра)
- имеет SemVer
- не дублирует OWNER/LOCK/VERSION внизу
- соответствует Naming Rules (или имеет approved exception)
- зарегистрирован в master-index слоя

---

## 5) MIGRATION PLAN (REQUIRED)
S0:
1) Устранить конфликт `00__*` в `02_STANDARDS/`:
   - `00__DOC_REGISTRY.md` → становится NON-CANON alias (указатель)
   - канон: `01__DOC_REGISTRY.md` (этот файл)
   - `00__MASTER_INDEX__UNIVERSE_ENGINE.md` → `02__MASTER_INDEX__UNIVERSE_ENGINE.md`

2) Проставить UID/шапку/semver всем документам из таблицы:
   - UID в шапке = DOC_UID из этой таблицы
   - VERSION минимум `1.0.0` (если не определено иначе)
   - убрать нижние дубли OWNER/LOCK/VERSION

S1:
3) Нормализовать имена протоколов/темплейтов/глоссария под `NN__...md` или зафиксировать исключения.

---

## FINAL RULE (LOCK)
Этот реестр — канонический инвентарь документов STANDARDS.
Любая правка — изменение канона и проходит Canon Protocol.
--- END.
