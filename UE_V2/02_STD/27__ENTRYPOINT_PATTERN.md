# 27__ENTRYPOINT_PATTERN

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: STD
UID: UE.V2.STD.ENTRYPOINT_PATTERN.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Единый паттерн "ENTRYPOINT" для запуска реалмов/доменов/процессов без блуждания и без перегруза контекста.

---

## [M] INTENT
Сделать вход в любую область системы (KB/REALM/DOMAIN/PIPE) одинаковым:
- коротко
- детерминированно
- через индексы
- без сканирования дерева и без огромных списков

---

## [M] DEFINITIONS
- ENTRYPOINT: короткий файл-вход, который ведёт в малые индексы и задаёт правила входа.
- REALM: область сущностей (ORC/CTL/VAL/QA/SPC/ENG…).
- DOMAIN: область задач (MUSIC/VIS/LOR/REL/CORE).
- IDX: малый индекс, который ведёт к конкретным файлам.

---

## [M] ENTRYPOINT TYPES
T1) SYSTEM ENTRYPOINT:
- 00_BOOT/00__START.md (единственный запуск задач)

T2) DOMAIN ENTRYPOINT:
- IDX_DOMAIN (например IDX_MUSIC), который даёт быстрый вход в пайпы/сущности домена

T3) REALM ENTRYPOINT:
- вход в реалм сущностей (например ORC_ENTRY), который ведёт в индекс реалма

T4) KB ENTRYPOINT:
- KB_NAV_ROOT, который ведёт в индексы модулей и scope-профили

---

## [M] WHAT ENTRYPOINT MUST CONTAIN
Обязательные секции:
1) INTENT (1–5 строк)
2) LOAD_POLICY (anti-noise)
3) PRIMARY LINKS (максимум 7–12 ссылок):
   - 1 главный индекс (IDX или NAV_ROOT)
   - 1–3 ключевых файла входа (если нужно)
   - 1 ссылка на правила/стандарт (если релевантно)
4) GATES (PASS/GAP/STOP кратко)

---

## [M] WHAT ENTRYPOINT MUST NOT CONTAIN
Запрещено:
- длинные списки всех сущностей реалма/домена
- копирование содержимого сущностей
- попытки заменить индекс (ENTRYPOINT не индексирует, он ведёт в индекс)
- “много ссылок на всякий случай”

---

## [M] ANTI-NOISE LOAD POLICY (CANON)
- ALWAYS: открыть ENTRYPOINT -> затем 1 нужный IDX -> затем 1–3 целевых файла
- NEVER: обход IDX и сканирование дерева папок
- TOKEN-FIRST: любые большие знания сворачивать в токены (KB_TOKEN / STEP_TOKEN)

---

## [M] RECOMMENDED LINK SHAPE
- Если нужно на "всё" -> ссылка на IDX_DOMAIN или NAV_ROOT
- Если нужно на "семью" -> ссылка на семейный индекс
- Если нужно на "одну сущность" -> ссылка на файл сущности

---

## [M] GATES
PASS если:
- ENTRYPOINT короткий и ведёт в малые IDX
GAP если:
- отсутствует нужный IDX/ENTRYPOINT для домена/реалма
REWORK если:
- ENTRYPOINT раздут или содержит длинные списки
STOP если:
- ENTRYPOINT недоступен (критичный для запуска в конкретном контексте)
