# MARKING STANDARD — DOC CONTROL (REFERENCE MODULE)

FILE: 02_STANDARDS/06_MARKING_STANDARDS/08__DOC_CONTROL.md
SCOPE: Universe Engine
LAYER: 02_STANDARDS/06_MARKING_STANDARDS
DOC_TYPE: STANDARD
STANDARD_TYPE: MARKING_MODULE
MARKING_FAMILY: DOC_CONTROL
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.MRK.DOC_CONTROL.001
OWNER: SYSTEM
ROLE: Compact marking reference for DOC CONTROL. Not a SoT. Provides quick markers and checklists aligned with the canonical DOC CONTROL standard.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Clarified SoT vs marking role, removed pseudo-navigation, added compact marker blocks + checklist, aligned with Doc Control Standard."
- REASON: "Marking modules must not act as navigation sources; they must be safe, compact references."
- IMPACT: "Less ambiguity: operators use this as quick card; tooling uses canonical standard."
- CHANGE_ID: UE.CHG.2026-01-20.MRK.DOCCTRL.001

---

## 0) PURPOSE (LAW)
Этот файл — **маркировочный модуль** (короткая карточка).
Он не заменяет и не переопределяет канонический стандарт.

SoT (authority):
- `02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md`
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

---

## 1) WHAT THIS IS / WHAT THIS IS NOT

### 1.1 This IS
- Быстрая справка по обязательным полям header.
- Напоминалка по запретам (anti-duplication).
- Мини-чеклист перед коммитом.

### 1.2 This is NOT
- Не навигационный индекс.
- Не “единая точка истины”.
- Не место для путей/линков как “главной навигации” (кроме явного указания SoT выше).

---

## 2) DOC CONTROL MARKERS (QUICK CARD)

### 2.1 Mandatory base fields (minimum)
Документ контролируемый системой должен иметь в header:
- FILE
- SCOPE
- LAYER
- DOC_TYPE
- LEVEL
- STATUS
- LOCK
- VERSION
- UID
- OWNER
- ROLE
- CHANGE_NOTE (DATE/TYPE/SUMMARY/REASON/IMPACT/CHANGE_ID)
- `---` (separator after header)

### 2.2 Header truth (ABSOLUTE)
- Header = единственная истина по метаданным.
- Запрещено повторять мета-поля ниже header.

Примеры запрещённого:
- `FINAL RULE (LOCK) LOCK: FIXED`
- повтор `OWNER/LOCK/STATUS/VERSION/UID` в конце файла
- “дубли-шапки” внутри тела

### 2.3 Allowed body content
В теле — только:
- правила, законы, определения, процедуры,
- ссылки на authority/related docs (если разрешено),
- примеры (без повторов меты).

---

## 3) SAFE XREF RULE (FOR MARKING MODULES)
Если этот модуль упоминает документы:
- по умолчанию **UID-only** (без ссылок),
- RAW даётся только:
  - если это явно authority link (как в разделе 0),
  - или если scope разрешает и это нужно для выполнения.

Иначе модуль превращается в “скрытый индекс”, что запрещено.

---

## 4) PRE-COMMIT CHECKLIST (MIN)

- [ ] `FILE:` совпадает с реальным путём файла.
- [ ] Все mandatory поля в header присутствуют.
- [ ] UID соответствует правилам UID law (канонический формат).
- [ ] Нет повторов метаданных в теле.
- [ ] CHANGE_NOTE заполнен и содержит CHANGE_ID.
- [ ] Если документ является INDEX/REGISTRY — existence rule и nav contract указаны.

---

## 5) END
This marking module is a compact reference. Authority remains the canonical Doc Control standard.
