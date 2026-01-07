# REL POLICY + XREF (MARKING MODULE) (CANON)
FILE: 02_STANDARDS/06_MARKING_STANDARDS/05__REL_POLICY_XREF.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: MODULE
MODULE_TYPE: MARKING
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.MOD.MARKING.REL_XREF.605
OWNER: SYSTEM
ROLE: Marking module that provides practical guidance and patterns for writing XREF/REL records in documents, including edge cases (external refs, alias pointers, deprecation chains). Extends REL/XREF SoT.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Модуль XREF: практические паттерны, мини-шаблоны, внешние ссылки, alias pointers, deprecation цепочки"
- REASON: "Нужен единый стиль ссылок и меньше ошибок"
- IMPACT: "All docs with relations"

---

## XREF (UID-first)
XREF: UE.STD.SPEC.REL_XREF.104 | extends | practical marking details for XREF | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md
XREF: UE.STD.MOD.MARKING.STORAGE_MAP.602 | references | alias pointer marking | 02_STANDARDS/06_MARKING_STANDARDS/02__STORAGE_MAP.md

---

## 0) PURPOSE
Этот модуль отвечает на вопрос “как писать XREF правильно в реальных файлах”:
- где размещать XREF блок
- как делать короткие XREF без лишнего шума
- как оформлять внешние источники
- как оформлять alias pointers и deprecation цепочки
- как избегать “битых” ссылок и двусмысленности

---

## 1) WHERE TO PUT XREF
Рекомендуемое место:
- сразу после Purpose/Authority (верхняя часть документа)

Стандартный заголовок:
- `## XREF (UID-first)`

---

## 2) MINIMAL XREF LINE (PREFERRED)
Минимальная корректная строка:
- `XREF: <UID_TARGET> | <REL_TYPE> | <WHY>`

Добавления (опционально):
- `| <PATH>`
- `| <RAW>`

Рекомендация:
- PATH лучше RAW, RAW только как reference.

---

## 3) MINI-PATTERNS (COPY)
### 3.1 depends_on (common)
`XREF: <UID> | depends_on | <why> | <path>`

### 3.2 governs (law → doc)
`XREF: <LAW_UID> | governs | <why> | <path>`

### 3.3 extends (module → SoT) (mandatory for modules)
`XREF: <SOT_UID> | extends | details module | <path>`

### 3.4 references (soft link)
`XREF: <UID> | references | background/context | <path>`

### 3.5 deprecated_by (mandatory for deprecated)
`XREF: <UID_NEW> | deprecated_by | migration target | <path>`

### 3.6 non_canon_alias_of (legacy pointers)
`XREF: <UID_CANON> | non_canon_alias_of | legacy filename alias | <path>`

---

## 4) EXTERNAL REFERENCES (ALLOWED EDGE CASE)
Если ссылка на внешний источник (вне системы):
- UID отсутствует, поэтому используем формат “EXTERNAL_REF” блоком, а не XREF строкой.

Рекомендуемый формат:
`EXTERNAL_REF: <url> | TYPE: <paper|site|video|...> | WHY: "<...>"`

Правило:
- Внутренние связи — только XREF UID-first.
- Внешние — только через EXTERNAL_REF.

---

## 5) ALIAS POINTER FILES (LEGACY)
Alias pointer файл обязан:
- иметь `CANON_TARGET_UID` и `CANON_TARGET`
- иметь XREF `non_canon_alias_of`
- не содержать “контент стандарта”

Минимальный XREF:
`XREF: <UID_CANON> | non_canon_alias_of | legacy alias pointer | <path-to-canon>`

---

## 6) DEPRECATION CHAINS (RULE)
Если A deprecated_by B, и B deprecated_by C:
- A должен ссылаться напрямую на B (as immediate target)
- допускается доп. ссылкой указать C как “final target”, но only references

Пример:
- `XREF: UID_B | deprecated_by | immediate migration | path_B`
- `XREF: UID_C | references | final target (chain) | path_C`

---

## 7) LINK HYGIENE RULES
### 7.1 WHY field must be meaningful
WHY не должен быть пустым или “see above”.

### 7.2 Avoid path-only links
Если есть UID — всегда ставим UID.

### 7.3 Raw links are brittle
RAW links разрешены, но не обязательны и не являются SoT.

---

## 8) COMMON FAILURES (ANTI-PATTERNS)
Запрещено:
- `XREF: <path only>` (без UID, если это внутренний объект)
- “references” вместо “extends” для module→SoT
- “supersedes” без MAJOR причины
- circular authority: SoT depends_on module

---

## 9) MIGRATION NOTES
S0:
- во всех mark modules добавить обязательный `extends` на их SoT
S1:
- внешние ссылки вынести в EXTERNAL_REF блоки, а не смешивать с XREF

---

## FINAL RULE (LOCK)
Этот модуль расширяет REL/XREF SoT и задаёт практику записи ссылок.
Изменения формата строки XREF = MAJOR по умолчанию.
--- END.
