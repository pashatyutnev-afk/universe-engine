# FILE: UE_V2/05_KB/00__KB_START.md
SCOPE: UE_V2
LAYER: 05_KB
DOC_TYPE: ENTRYPOINT
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.KB.START.001
OWNER: SYSTEM
TITLE: KB START

## MARKERS
- [M] INTENT
- [M] KB_SCOPE
- [M] KB_IO
- [M] KB_ACCESS
- [M] KB_GATES

## [M] INTENT
KB = слой определений и норм (не “контент ради текста”). Используется для:
- терминов/метрик/порогов
- границ допустимых источников
- форматов входов/выходов
- доменных справочников AUD/VIS/LOR

## [M] KB_SCOPE
KB хранит только:
- definitions (DEF)
- constraints (CST)
- mappings (MAP)
- thresholds (THR)
- examples (EX) — коротко, 1–3 строки

KB НЕ хранит:
- длинные рассуждения
- “истории”, “введение”, “мотивацию”
- навигацию по репо (это 04_NAV)
- правила оформления документов (это 02_STD)

## [M] KB_IO
Входы: только из 02_STD/08__KB_SCOPE + доменные KB_*.
Выход: “KB Extract” — короткая подборка нужных DEF/THR/MAP под задачу.

## [M] KB_ACCESS
Роутинг:
- audio definitions → 05__KB_AUD
- visual definitions → 06__KB_VIS
- lore definitions → 07__KB_LOR
Если нет определения → GAP: добавить DEF/THR/MAP в доменный KB.

## [M] KB_GATES
- Noise budget: PASS если 1 объект = 1 определение/порог/маппинг
- Marker integrity: PASS если все секции [M] присутствуют
- No navigation bloat: PASS если нет списков файлов/папок
