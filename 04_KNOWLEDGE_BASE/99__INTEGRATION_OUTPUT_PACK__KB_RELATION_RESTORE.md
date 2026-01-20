# 99__INTEGRATION_OUTPUT_PACK__KB_RELATION_RESTORE.md

SCOPE: Universe Engine (Games volume)
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: OUTPUT_PACK
PACK_TYPE: INTEGRATION_RESTORE
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.PACK.REL_RESTORE.099
OWNER: INTEGRATION_PACKER_SPC
ROLE: Integration output pack that restores a consistent KB relation subsystem (REL vocabulary + relation model + graph template + authoring quickstart). Defines what files belong to the pack, where they live, and how to register/validate them.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Packaged KB relation restore set with unified formats + placement map + registration checklist + validation gates."
- REASON: "Previous drafts were inconsistent and scattered; need a deterministic restore set."
- IMPACT: "KB relation authoring becomes stable; graph audits become repeatable; onboarding becomes faster."
- CHANGE_ID: UE.CHG.2026-01-20.KB.REL_RESTORE.099

---

## 0) PURPOSE (LAW)
Этот OUTPUT PACK фиксирует **восстановительный набор** для подсистемы KB связей:
- единый словарь типов связей (REL_TYPE),
- единая модель отношений (как кодировать REL),
- единый шаблон артефакта графа,
- единый quickstart для автора.

Цель:
- чтобы KB модули и связи сразу делались “как надо” и не разваливались из-за разных форматов.

---

## 1) KB SCOPE (REQUIRED)
KB INPUTS:
- Ситуация “REL документы/правила сделаны как попало” или отсутствуют
- Потребность стабилизировать REL и аудит

KB OUTPUTS:
- Набор файлов restore-пака (см. раздел 2)
- Инструкция размещения + регистрации + проверки

KB BOUNDARIES:
- Пак не заменяет KB master-index и не делает регистрацию автоматически
- Пак не создаёт новые сущности вне перечисленных файлов
- Пак не меняет ROOT-INDEX и не расширяет RAW link base

KB RAW REFERENCES (IF ANY):
- KB MASTER INDEX:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
- KB RULES:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

---

## 2) PACK CONTENTS (CANON)
Ниже — канонический состав пакета и точные пути размещения.

### 2.1 Files in pack (REQUIRED SET)
A) Authoring guide (quickstart)
- PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/16__KB_AUTHORING_QUICKSTART.md`
- UID: UE.KB.GUIDE.AUTHORING.016
- ROLE: единый “как писать KB”

B) Relation types dictionary
- PATH: `04_KNOWLEDGE_BASE/04__RELATION_TYPES_CANONICAL_DICTIONARY.md`
- UID: UE.KB.DICT.REL_TYPES.004
- ROLE: единый словарь REL_TYPE

C) Relation model standard
- PATH: `04_KNOWLEDGE_BASE/24__KB_RELATION_MODEL_STANDARD.md`
- UID: UE.KB.STD.REL_MODEL.024
- ROLE: единый стандарт как кодировать REL (UID-only, WHY, separation)

D) Relation graph artifact template
- PATH: `04_KNOWLEDGE_BASE/06__KB_RELATION_GRAPH_TEMPLATE.md`
- UID: UE.KB.TPL.REL_GRAPH.006
- ROLE: шаблон отдельного артефакта “граф отношений”

E) Compliance report (this pack companion)
- PATH: `04_KNOWLEDGE_BASE/98__COMPLIANCE_REPORT__KB_RELATION_RESTORE.md`
- UID: UE.KB.REPORT.REL_RESTORE.098
- ROLE: отчёт, что пак применён корректно

---

## 3) INSTALL / APPLY STEPS (RUNBOOK)
### 3.1 Place files
1) Разместить файлы строго по путям из раздела 2.1
2) Проверить, что имена файлов совпадают посимвольно

### 3.2 Register in KB master index
Добавить записи в:
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

Минимум: включить 4 основных документа (A–D) + отчёт (E).

### 3.3 Optional: register in KB governance realm index
Если у governance realm есть отдельный sub-index (если используется) —
добавить quickstart туда тоже.

---

## 4) REQUIRED CONSISTENCY RULES (PACK LAW)
### 4.1 Unified header format
Все файлы из пакета должны иметь:
- SCOPE/LAYER/DOC_TYPE/LEVEL/STATUS/LOCK/VERSION/UID/OWNER/ROLE
- CHANGE_NOTE с CHANGE_ID

### 4.2 NAV vs REL separation
- NAV (переходы) — только RAW ссылки и только в INTERFACES
- REL — только UID-only и WHY

### 4.3 Canonical REL_TYPE enforcement
REL_TYPE берётся только из словаря:
- UE.KB.DICT.REL_TYPES.004

---

## 5) POST-INSTALL CHECKLIST (MANDATORY)
### 5.1 Existence
- [ ] Все 5 файлов присутствуют в нужных путях
- [ ] Имена совпадают

### 5.2 Formatting
- [ ] Header заполнен в каждом файле
- [ ] CHANGE_ID заполнен в каждом файле

### 5.3 Semantic correctness
- [ ] REL documents не содержат URL в REL правилах
- [ ] NAV ссылки (если есть) только RAW

### 5.4 Registration
- [ ] Все файлы зарегистрированы в KB master index

---

## 6) ROLLBACK (OPTIONAL)
Если нужно откатить:
- удалить записи из master-index
- удалить файлы restore-пака
- восстановить предыдущие версии (если они были)

---

## 7) INTERFACES (RAW-ONLY)
- KB MASTER INDEX
  - PURPOSE: Register pack files in KB canonical registry
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

- KB RULES
  - PURPOSE: Ensure pack obeys KB governance
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

---

## 8) RELATIONS (UID-ONLY)
- FROM_UID: UE.KB.PACK.REL_RESTORE.099
  REL_TYPE: depends_on
  TO_UID: UE.KB.DICT.REL_TYPES.004
  WHY: Pack requires canonical REL vocabulary.

- FROM_UID: UE.KB.PACK.REL_RESTORE.099
  REL_TYPE: governed_by
  TO_UID: UE.KB.STD.REL_MODEL.024
  WHY: Pack implementation follows relation model standard.

- FROM_UID: UE.KB.PACK.REL_RESTORE.099
  REL_TYPE: maps_to
  TO_UID: UE.KB.TPL.REL_GRAPH.006
  WHY: Graph template is the pack’s audit artifact format.

- FROM_UID: UE.KB.PACK.REL_RESTORE.099
  REL_TYPE: governed_by
  TO_UID: UE.KB.GUIDE.AUTHORING.016
  WHY: Authoring guide defines how to use the restored relation subsystem.

---

## 9) COMPLIANCE CHECKLIST (REQUIRED)
- [ ] Pack contents match section 2.1
- [ ] Paths match exactly
- [ ] Files registered in KB master index
- [ ] REL uses UID-only + canonical REL_TYPE + WHY
- [ ] NAV uses RAW-only (if present)

---

## 10) OPTIONAL CHANGE LOG
- 2026-01-20 — CREATE — v1.0.0

---
## END
