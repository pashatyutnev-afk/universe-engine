# PRIORITY S0–S3 (MARKING MODULE) (CANON)
FILE: 02_STANDARDS/06_MARKING_STANDARDS/04__PRIORITY_S0_S3.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: MODULE
MODULE_TYPE: MARKING
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.MOD.MARKING.PRIORITY_S0_S3.604
OWNER: SYSTEM
ROLE: Marking module defining the Priority scale S0–S3 for issues, migrations, compliance gaps, and work items. Establishes meaning, response expectations, and where to apply these tags.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Модуль Priority S0–S3: значения, критерии, где применять, отличие от других шкал (например NAT strictness)"
- REASON: "Нужен единый язык критичности проблем и работ"
- IMPACT: "All layers: indices, registries, migration notes, governance"

---

## XREF (UID-first)
XREF: UE.STD.SPEC.DOC_REGISTRY.107 | references | compliance states often pair with priority | 02_STANDARDS/01_SPECIFICATIONS/07__DOC_REGISTRY_STANDARD.md
XREF: UE.STD.SPEC.DOC_CONTROL.103 | references | where markers can be placed | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
XREF: UE.STD.SPEC.NAT_GATES.106 | references | NAT uses S0–S3 as strictness, not priority | 02_STANDARDS/01_SPECIFICATIONS/06__NATURALNESS_GATES_STANDARD.md

---

## 0) PURPOSE
Этот модуль определяет шкалу приоритета S0–S3:
- как отмечать критичность проблем/несоответствий/миграций
- какие ожидания реакции у каждого уровня
- где применять эти маркеры в документах

---

## 1) PRIME RULE (ABSOLUTE)
`PRIORITY S0–S3` = критичность проблемы/работы.

Это НЕ:
- “уровень качества”
- “уровень строгости NAT” (там это strictness)
- “уровень важности персонажа/сцены”

---

## 2) PRIORITY SCALE (CONTROLLED)
### S0 — BLOCKER (STOP THE CANON)
- Meaning: блокер, ломает канон или систему идентичности/существования
- Examples:
  - дубликаты UID
  - две entrypoint точки в одном слое
  - отсутствие master-index / broken existence rule
  - конфликт номеров NN* в папке, делающий навигацию неоднозначной
- Expectation: чинить первым, до любых новых расширений

### S1 — HIGH (MAJOR RISK)
- Meaning: высокая критичность, создаёт устойчивую путаницу или риск ошибок
- Examples:
  - документ в индексе без валидного Doc Control header
  - broken XREF/REL политика (ссылки без UID)
  - крупные дубли смысла (второй документ “про то же”)
- Expectation: исправить в ближайшем цикле нормализации

### S2 — MEDIUM (QUALITY/MAINTENANCE)
- Meaning: средняя критичность, ухудшает качество/скорость, но не ломает канон
- Examples:
  - неполные описания, слабые формулировки
  - устаревшие raw links
  - недостающие примеры
- Expectation: чинить по мере работ, когда заходим в область

### S3 — LOW (NICE-TO-HAVE)
- Meaning: косметика/улучшение
- Examples:
  - стилистика, выравнивание секций
  - дополнительные пояснения
- Expectation: опционально

---

## 3) WHERE TO APPLY PRIORITY MARKERS
### 3.1 In registries (recommended)
В Doc Registry строке можно добавлять:
- `NOTES: "S1 — missing header normalization"`

### 3.2 In indices (allowed)
В master-index рядом с документом:
- пометка “(S0 fix needed)” допускается, но индекс не должен превращаться в backlog

### 3.3 In migration sections (best)
В секциях `MIGRATION NOTES`:
- ставить приоритет на каждый пункт

Пример:
- `S0: Fix duplicate entrypoint indexes in KB layer`
- `S1: Normalize legacy index aliases`
- `S2: Add examples for registry records`

---

## 4) PRIORITY + COMPLIANCE (COMMON PAIRS)
Типовые пары:
- `COMPLIANCE: INVALID` почти всегда `S0`
- `COMPLIANCE: PENDING` обычно `S1/S2`
- `COMPLIANCE: OK` — priority не нужен

---

## 5) ESCALATION RULE
Если проблема S2 вызывает реальные ошибки навигации/идентификации → повышать до S1/S0.

---

## 6) MIGRATION NOTES
S0:
- убрать путаницу между PRIORITY S0–S3 и NAT strictness S0–S3: всегда писать префикс
  - `PRIORITY: S1`
  - `NAT_STRICTNESS: S2`

---

## FINAL RULE (LOCK)
Priority S0–S3 — единый язык критичности проблем/работ в Universe Engine.
Любая правка значений шкалы = изменение канона.
--- END.
