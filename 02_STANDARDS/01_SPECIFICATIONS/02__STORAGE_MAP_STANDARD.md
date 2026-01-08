# STORAGE MAP STANDARD (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.2.0
UID: UE.STD.SPEC.STORAGE_MAP.001
OWNER: SYSTEM
ROLE: How layers describe allowed storage topology + prohibited zones + strict-mode compatibility

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "Removed outdated 00__INDEX__STANDARDS.md reference. Defined strict single-index mode as compatible option."
- REASON: "Совместимость с текущей структурой 02_STANDARDS и строгим режимом KB."
- IMPACT: "No broken entrypoint assumptions; layers may be stricter."

---

## PURPOSE (LAW)
Стандарт определяет, как описывать карту хранения (Storage Map) для слоя:
- разрешённые зоны (whitelist)
- запрещённые зоны (banlist)
- политика изменений зон

---

## ENTRYPOINT RULE (LAYER MASTER)
Каждый слой должен иметь канонический entrypoint (master-index/entry map) внутри слоя.
Пример для `02_STANDARDS`:
- `00__MASTER_INDEX__UNIVERSE_ENGINE.md`

NOTE:
Legacy/alias файлы могут существовать, но не должны быть источником истины.

---

## MINIMUM STORAGE MAP STRUCTURE (REQUIRED)
1) ROOT
2) ALLOWED ZONES (WHITELIST)
3) PROHIBITED (HARD BAN)
4) CHANGE POLICY
5) COMPATIBILITY NOTES (если слой строже)

---

## STRICT MODE (COMPATIBLE)
Слой может быть строже стандарта.

### STRICT SINGLE-INDEX / NO-SUB-INDEX
Если слой включает strict mode:
- existence и навигация определяются только одним master-index файла слоя
- любые sub-indexes запрещены
- навигационные ссылки (PATH/RAW/URL) допускаются только в master-index

Это валидно и совместимо со стандартами при соблюдении UID-first.

--- END.
