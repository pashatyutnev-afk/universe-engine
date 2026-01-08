# STORAGE MAP STANDARD (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.SPEC.STORAGE_MAP.001
OWNER: SYSTEM
ROLE: Defines how layers describe allowed storage topology + prohibited zones

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "Removed reference to non-existing 02_STANDARDS/00__INDEX__STANDARDS.md. Added strict-layer compatibility (Single-Index mode) and clarified entrypoint for 02_STANDARDS."
- REASON: "Синхронизация стандарта с реальной структурой 02_STANDARDS и строгим режимом KB."
- IMPACT: "No broken entrypoint examples; layers may be stricter than baseline."

---

## PURPOSE (LAW)
Стандарт определяет, как описывать карту хранения (Storage Map) для слоя:
- разрешённые зоны (whitelist)
- запрещённые зоны (banlist)
- правила существования и навигации (если слой вводит строгий режим)

---

## BASE DEFINITIONS
- ROOT: корневая папка слоя.
- ZONE: логическая область хранения (папка или диапазон файлов).
- STORAGE MAP DOC: документ, который описывает зоны и запреты слоя.
- EXISTENCE MAP: список “что существует” (обычно индекс слоя).

---

## ENTRYPOINT EXAMPLE (02_STANDARDS)
Канонический вход в слой 02_STANDARDS задаётся master-index’ом слоя:
- `02_STANDARDS/00__MASTER_INDEX__UNIVERSE_ENGINE.md`

NOTE:
Если в слое есть legacy/alias entrypoints — они не должны быть источником истины по существованию.

---

## MINIMUM STORAGE MAP STRUCTURE (REQUIRED)
Каждый Storage Map документа слоя должен содержать:

1) ROOT
2) ALLOWED ZONES (WHITELIST)
3) PROHIBITED (HARD BAN)
4) CHANGE POLICY (как добавляются зоны)
5) COMPATIBILITY NOTES (если слой строже стандарта)

---

## STRICT LAYER COMPATIBILITY (IMPORTANT)
Слой может быть строже базового стандарта.

### STRICT MODE: SINGLE-INDEX / NO-SUB-INDEX
Если слой объявляет строгий режим:
- existence и навигация определяются только одним master-index файла слоя
- любые sub-indexes запрещены
- навигационные ссылки (PATH/RAW/URL) могут быть разрешены только в master-index

Это валидный режим и считается совместимым со стандартами.

---

## RECOMMENDED ZONE DESCRIPTION FORMAT
- ZONE: <name>
- TYPE: <folder | range | file>
- INTENT: <why it exists>
- RULES: <must/ban list, short>

---

## PROHIBITED PATTERNS (RECOMMENDED)
Storage Map должен явно запрещать:
- “локальные реестры существования” (sub-indexes) если слой в strict mode
- неучтённые папки/диапазоны
- дублирование SoT по existence (два разных индекса)

--- END.
