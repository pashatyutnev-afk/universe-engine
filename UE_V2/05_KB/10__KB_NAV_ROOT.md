# 10__KB_NAV_ROOT

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: KB / NAV
UID: UE.V2.KB.NAV_ROOT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Единственная точка входа в KB навигацию. Ведёт в scope-профили и малые индексы модулей. Запрещает блуждание по папкам.

---

## [M] INTENT
Сделать KB библиотекой, а не свалкой:
- вход только через scope-гейт
- выбор модулей только через малые индексы
- использование KB только через KB_TOKEN

---

## [M] REQUIRED FLOW (SCOPE-GATE)
1) определить KB_SCOPE_ID (из REG или ROUTE/PLAN)
2) открыть:
   - UE_V2/05_KB/09__KB_SCOPE_PROFILES.md
3) выбрать модули через индекс:
   - UE_V2/05_KB/11__IDX_KB_MODULES_BY_DOMAIN.md
   - или UE_V2/05_KB/12__IDX_KB_MODULES_BY_TOPIC.md
4) взять PICKSET 3–7 модулей
5) собрать KB_TOKEN (5–15 пунктов) и закрыть KB

---

## [M] ENTRYPOINT LINKS
- KB boundaries: UE_V2/05_KB/04__KB_BOUNDARIES.md
- KB sources: UE_V2/05_KB/08__KB_SOURCES.md
- KB scope profiles: UE_V2/05_KB/09__KB_SCOPE_PROFILES.md

- IDX by domain: UE_V2/05_KB/11__IDX_KB_MODULES_BY_DOMAIN.md
- IDX by topic: UE_V2/05_KB/12__IDX_KB_MODULES_BY_TOPIC.md

OPTIONAL:
- IDX scopes (если введёшь): UE_V2/05_KB/13__IDX_KB_SCOPES.md
- KB module format (если введёшь): UE_V2/05_KB/14__KB_MODULE_FMT.md

---

## [M] ANTI-NOISE POLICY
- Запрещено:
  - ходить по папкам KB
  - открывать десятки модулей “на всякий случай”
- Разрешено:
  - открыть 1 индекс + 3–7 модулей по scope
- Любой вывод из KB должен быть свернут в KB_TOKEN.

---

## [M] GATES
PASS если:
- KB используется через KB_TOKEN и scope-гейт
REWORK если:
- KB читается “в лоб” пачкой файлов
GAP если:
- отсутствуют индексы 11/12 или scope-профили
STOP если:
- систематическое нарушение scope (ломает KB)
