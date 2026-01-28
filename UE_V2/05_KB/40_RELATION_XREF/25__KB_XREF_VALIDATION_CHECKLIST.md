# KB XREF VALIDATION CHECKLIST (CANON)

FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/25__KB_XREF_VALIDATION_CHECKLIST.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 04_KNOWLEDGE_BASE
REALM: 40_RELATION_XREF
DOC_TYPE: CHECKLIST
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.XREF.CHK.025
OWNER: SYSTEM
ROLE: Deterministic checklist to validate KB cross-references (XREF) and KB consumption pointers in runtime artifacts. Ensures RAW-only pointers, provenance markers, module state legality, and no ghost references.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Introduced enforceable KB↔XREF validation checklist: RAW pointers, provenance markers, state legality, and anti-ghost rules."
- REASON: "KB usage was failing due to missing provenance, stale pointers, and undocumented consumption."
- IMPACT: "KB crossrefs become auditable and safe for ORC/CTL/VAL pipelines."
- CHANGE_ID: UE.CHG.2026-01-20.KB.XREFCHK.025

---

## 0) PURPOSE (LAW)
Этот чеклист проверяет, что:
- KB ссылки используются законно (RAW-only),
- KB источники имеют provenance markers (если есть non-user content),
- KB модули имеют допустимое состояние,
- runtime артефакты, которые потребляют KB, явно указывают KB_SCOPE_RAW,
- нет “призрачных” ссылок (на несуществующие/незарегистрированные объекты).

---

## 1) REQUIRED LAWS / REFERENCES (RAW)
KB RULES  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

KB SOURCE LOCK / NO FANTASY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/12__KB_SOURCE_LOCK_NO_FANTASY.md

KB XREF RULES  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/07__KB_XREF_RULES.md

KB MASTER INDEX (entrypoint)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

KB REL VALIDATION CHECKLIST (companion)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/40_RELATION_XREF/26__KB_REL_VALIDATION_CHECKLIST.md

---

## 2) SCOPE (WHAT THIS CHECKLIST APPLIES TO)
### 2.1 KB XREF artifacts
- любые карты соответствий KB↔Entities (SPC/ENG/ORC/CTL/VAL/QA)
- любые таблицы “что где лежит” для KB scope
- любые KB relation graph templates/records

### 2.2 Runtime consumption artifacts (must be checked if they consume KB)
- ORC пайплайны, которые берут корпус/правила из KB
- CTL/VAL, которые требуют provenance/status/state
- Release/Prompt/Pack документы, если они ссылаются на KB источники

---

## 3) STOP CONDITIONS (CHECKLIST CONTEXT)
Если обнаружено:
- RAW missing
- marker not confirmed
- input absent
то результат чеклиста: FAIL и возврат на исправление.

---

## 4) CHECKLIST — KB POINTER INTEGRITY (RAW-ONLY)
### CHK-01 RAW-only pointers
- [ ] Все ссылки на KB начинаются с raw.githubusercontent.com
- [ ] Нет ссылок на index-файлы “как URL” (только на реальные документы)
- [ ] Нет локальных путей без RAW (никаких “04_KNOWLEDGE_BASE/... без ссылки”)

FAIL_CLASS if broken: marker not confirmed

### CHK-02 Pointer resolvable
- [ ] Каждая KB ссылка указывает на существующий файл (не 404)
- [ ] Нет ссылок на папку вместо файла (если не оговорено как folder-pointer)

FAIL_CLASS if broken: RAW missing

---

## 5) CHECKLIST — KB REGISTRATION (NO GHOST)
### CHK-03 Master index registration
- [ ] KB объект (модуль/под-индекс/realm) зарегистрирован в `00__INDEX__KNOWLEDGE_BASE.md`
- [ ] Если объект не зарегистрирован — он не может быть “канонической точкой входа”

FAIL_CLASS if broken: marker not confirmed

### CHK-04 No duplicate entrypoints
- [ ] Нет параллельных “master index” для KB слоя
- [ ] Нет “второго главного README”, который объявляет себя entrypoint

FAIL_CLASS if broken: policy violation

---

## 6) CHECKLIST — PROVENANCE (SOURCE LOCK COMPLIANCE)
### CHK-05 Provenance markers present for non-user content
Если KB объект содержит non-user content или на него ссылается runtime как на источник:
- [ ] KB_SOURCE_RAW присутствует
- [ ] SOURCE_STATUS присутствует и корректен (PD_CONFIRMED | LICENSE_CONFIRMED)
- [ ] SOURCE_NOTE присутствует
- [ ] FULL_TEXT_ALLOWED присутствует только если реально нужен полный текст

FAIL_CLASS if broken: marker not confirmed

### CHK-06 No external claims without KB_SOURCE_RAW
- [ ] В runtime документах (prompt/release/pack) нет утверждений “источник такой-то” без KB_SOURCE_RAW

FAIL_CLASS if broken: policy violation

---

## 7) CHECKLIST — MODULE STATE LEGALITY
### CHK-07 Module state declared
- [ ] Каждый KB модуль имеет state (как требует module state system)
- [ ] State допускает использование в runtime (по правилам состояния)

FAIL_CLASS if broken: marker not confirmed

### CHK-08 Deprecation handled
Если KB модуль помечен deprecated/replaced:
- [ ] Есть явный pointer на replacement
- [ ] XREF записи обновлены или имеют deprecation pointer

FAIL_CLASS if broken: marker not confirmed

---

## 8) CHECKLIST — RUNTIME CONSUMPTION INTERFACE (KB_SCOPE_RAW)
### CHK-09 Explicit KB_SCOPE_RAW in consumers
Для каждого ORC/CTL/VAL, который потребляет KB:
- [ ] Есть KB_SCOPE_RAW (входной pointer на KB модуль/элемент)
- [ ] Указан минимум: что именно берём (scope description)

FAIL_CLASS if broken: input absent

### CHK-10 Provenance block propagated when needed
Если consumer использует CORPUS/цитаты:
- [ ] В consumer артефакте повторён provenance блок (KB_SOURCE_RAW, SOURCE_STATUS, SOURCE_NOTE)
- [ ] Не добавлены “внешние строки” вне provenance

FAIL_CLASS if broken: marker not confirmed

---

## 9) CHECKLIST — XREF RECORD SHAPE (MINIMUM)
Каждая XREF запись (карта/таблица/граф) должна содержать минимум:
- [ ] FROM_ENTITY (UID или stable identifier)
- [ ] TO_KB_SCOPE (RAW pointer)
- [ ] REL_TYPE (из канонического словаря, если применимо)
- [ ] PURPOSE (зачем связь)
- [ ] STATUS/LOCK/VERSION (doc control)

FAIL_CLASS if broken: marker not confirmed

---

## 10) OUTPUT FORMAT (RESULT OF THIS CHECKLIST)
Результат проверки должен фиксироваться как минимум:

- RESULT: PASS | FAIL
- TARGET: (what was checked)
- FAIL_CLASS: (RAW missing | marker not confirmed | input absent | policy violation)
- FINDINGS:
  - bullet list
- REQUIRED_FIXES:
  - bullet list (empty if PASS)
- RETURN_TO:
  - document(s) that must be fixed (RAW)

---

END.
