# XREF INDEX — CROSSREF (CANON REGISTRY)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__INDEX__CROSSREF.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: INDEX
INDEX_TYPE: REALM_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.IDX.REALM.001
OWNER: SYSTEM
ROLE: Single canonical registry + navigation map for all XREF assets (maps, templates, records) in CROSSREF realm.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Initialized canonical XREF realm index with strict existence rule + primary map set registration."
- REASON: "Make routing, gate placement, and entity mapping discoverable without guessing."
- IMPACT: "XREF realm becomes auditable and deterministic for runtime navigation."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.IDX.001

---

## 0) PURPOSE (LAW)
Этот INDEX — единственная точка истины для слоя `90_XREF__CROSSREF`.
Он фиксирует:
- какие карты XREF существуют (CANON),
- какие шаблоны используются,
- какие файлы являются входными точками навигации (RAW-only).

---

## 1) ABSOLUTE NAV RULE
- Навигация только по RAW ссылкам.
- Нельзя угадывать пути/файлы вне этого реестра и ROOT LINK BASE.

---

## 2) EXISTENCE RULE (ABSOLUTE)
- Канон XREF существует только в рамках записей этого INDEX.
- Если файл/карта есть в репо, но не зарегистрирован здесь — NON-CANON / ignored.
- Если ссылка в этом INDEX ведёт на несуществующий файл → это GAP и требует ремонта.

---

## 3) ENTRYPOINTS (CANON)
00 — README: CROSSREF REALM  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__README__CROSSREF.md

00 — INDEX: CROSSREF REALM (THIS FILE)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__INDEX__CROSSREF.md

---

## 4) TEMPLATES (CANON)
00 — TEMPLATE: XREF INDEX  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__TEMPLATE__XREF_INDEX.md

00 — TEMPLATE: XREF RECORD  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__TEMPLATE__XREF_RECORD.md

---

## 5) PRIMARY MAP SET (MINIMUM CANON)
Этот набор считается минимально необходимым для детерминированного routing и gate placement.

01 — MAP: ENG → ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__MAP__ENG_to_ORC.md

02 — MAP: ORC → SPC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__MAP__ORC_to_SPC.md

03 — MAP: VALIDATION MATRIX  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md

04 — MAP: PIPELINES (intent → pipeline)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md

---

## 6) OPTIONAL / EXTENDED MAPS (POLICY)
Если появляется новый тип соответствий:
- создаём новый MAP-файл по шаблону,
- регистрируем здесь в отдельном блоке,
- только потом разрешаем рантайму на него ссылаться.

---

## 7) CHANGE POLICY (LOCK)
- Любые изменения: только PATCH + CHANGE_NOTE.
- Удаление/замена: только через deprecation pointer (если используется в процессе).
- Этот INDEX — LOCK: FIXED.

---  
END.
