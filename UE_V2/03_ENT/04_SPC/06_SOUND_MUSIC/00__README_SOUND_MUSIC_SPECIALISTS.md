# SPC FAMILY REALM — SOUND & MUSIC SPECIALISTS (CANON)
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/00__README_SOUND_MUSIC_SPECIALISTS.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
DOC_TYPE: README
INDEX_TYPE: FAMILY_REALM
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.REALM.SOUND_MUSIC.001
OWNER: SYSTEM
ROLE: Family realm definition + boundaries + navigation rules for SPC family `06_SOUND_MUSIC`

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established SOUND_MUSIC SPC family realm: responsibilities, boundaries, interfaces, KB scope, quality rules, and production handoffs."
- REASON: "Need deterministic audio pipeline roles: supervision, production, composition, songwriting, lyrics, arrangement, vocals, sound design, mix, mastering, and audio QA."
- IMPACT: "Sound & music production becomes coherent: consistent sonic identity, clear role ownership, and reliable deliverables across episodes and formats."
- CHANGE_ID: UE.CHG.2026-01-09.SPC.REALM.SOUND_MUSIC.001

---

## 0) PURPOSE (LAW)
Семейство `06_SOUND_MUSIC` отвечает за звук и музыку как систему:
- музыкальная супервизия и общая стратегия (что за музыкальный язык)
- продюсирование (как это собирается в треки/релизы)
- композиция (мелодия/гармония/структура)
- написание песен и текстов
- аранжировка и инструментовка
- вокал и постановка исполнения
- звук-дизайн (не музыка, а звуковая драматургия)
- сведение (mix) и мастеринг (master)
- аудио QA (техническое и качественное)

Цель семьи — сделать аудио **узнаваемым, управляемым и воспроизводимым**: чтобы “музыка и звук” поддерживали историю и продакшн без хаоса и дрейфа.

---

## 1) EXISTENCE + NAV RULE (MANDATORY)
- Специалист существует для системы **только если**:
  1) зарегистрирован в глобальном SPC INDEX:
     `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md`
  2) и файл лежит по каноническому пути
- Любые файлы в папке без регистрации — **NON-CANON / ignored**
- Каноническая навигация по семье — через RAW ссылки глобального SPC INDEX

---

## 2) FAMILY SCOPE
**FAMILY NAME:** SOUND & MUSIC SPECIALISTS  
**FAMILY PATH:** `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/`

### 2.1 Covered domains (what we DO)
- Music supervision (sonic identity, constraints, direction)
- Music production (tracks, demos, release-ready assets)
- Composition (themes, harmony, melody, structure)
- Songwriting & lyrics (songs as narrative tools)
- Arrangement & instrumentation
- Vocal direction & performance shaping
- Sound design (non-music audio: fx, texture, emphasis)
- Mixing & mastering
- Audio QA

### 2.2 Hard boundaries (what we DO NOT do)
- Не пишем сюжет/диалоги (это `02_NARRATIVE`), но можем поддерживать смысл/эмоцию звуком.
- Не задаём визуальный стиль (это `05_VISUAL`), но можем синхронизироваться по ритму/динамике.
- Не принимаем финальные монтажные решения видеоряда (это editing/montage), но выдаём аудио-ограничения/риски (sync, динамика).
- Не утверждаем канон мира (это `04_WORLD` + lore/governance), но соблюдаем.
- Не подменяем “Production audio” и “Deep music”: production синхрон/размещение ≠ композиторская глубина (смотри интерфейсы).

---

## 3) KNOWLEDGE BASE (KB) SCOPE (MANDATORY)
### 3.1 KB INPUTS (what this family reads)
- Realm: Sound & Music  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/04__SOUND_MUSIC.md
- Realm: Production Pipeline (для стыка с продакшном)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/05__PRODUCTION_PIPELINE.md
- Realm: Reference Glossary (термины)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/07__REFERENCE_GLOSSARY.md

### 3.2 KB OUTPUTS (what this family may contribute)
- Добавление унифицированных практик (если выявлены стабильные паттерны) в KB realms выше.
- Дополнение topic-доков по звуку/музыке (если будут зарегистрированы в KB Topics canon).

### 3.3 KB BOUNDARIES (what is NOT owned)
- Фактчекинг, научная достоверность, историческая точность — это `08__RESEARCH_FACT_CHECKING` realm и валидаторы.
- Визуальные решения, кадр, монтаж — не зона SOUND_MUSIC (только синхрон/ограничения).

---

## 4) INTERFACES (SYSTEM LINKS) — RAW ONLY
### 4.1 ENG (Engines) — typical support
- Production audio (sync/design/placement/clarity):  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md
- Deep music engines (composition/harmony/arrangement/vocal/mix/master):  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md

### 4.2 ORC — typical usage
ORC вызывает SOUND_MUSIC SPC когда нужно:
- определить sonic identity (Music Supervisor)
- произвести трек/демо/релизный ассет (Music Producer)
- написать музыку/песню/текст (Composer/Songwriter/Lyricist)
- сделать аранжировку/вокал (Arranger/Vocal Director)
- сделать звук-дизайн для сцен (Sound Designer)
- свести/замастерить (Mix/Mastering)
- прогнать QA (Audio QA)

### 4.3 QA / VAL gates
Типовые гейты:
- clarity & intelligibility (разборчивость)
- loudness & dynamics sanity (не убивает контент)
- sync sanity (попадание в моменты)
- consistency sanity (sonic identity не дрейфует)

---

## 5) FAMILY STANDARDS (MANDATORY RULES)
### 5.1 Anti-overlap (role separation)
- Music Supervisor: владелец sonic identity (правила и контроль дрейфа).
- Music Producer: владелец production pipeline трека/релиза.
- Composer: владелец музыкальной композиции (темы, гармония, структура).
- Songwriter: владелец песенной формы/хуков/структуры песни.
- Lyricist: владелец текста (смысл, ритм текста, голос).
- Arranger: владелец инструментовки/аранжировки.
- Vocal Director: владелец постановки вокального исполнения.
- Sound Designer: владелец non-music sound design (fx/texture/emphasis).
- Mix Engineer: владелец сведения (баланс, пространство, динамика).
- Mastering Engineer: владелец финального мастера (переводимость, громкость, финальный тон).
- Audio QA: владелец проверки качества/техники (ошибки, клипы, артефакты).

### 5.2 Sonic identity law
Любая музыка/звук должны иметь:
- узнаваемость (повторяемые принципы/мотивы/текстуры)
- ясность (главное слышно)
- цель (что поддерживает: эмоцию/инфо/ритм)
- контроль дрейфа (что считается “не нашим звуком”)

### 5.3 Production boundary (no editing decisions)
SOUND_MUSIC не принимает монтажных решений по видео.  
Мы выдаём только:
- синхрон-ограничения (где MUST hit)
- риски (если темп монтажа ломает музыку/смысл)
- варианты адаптации аудио под монтаж (но не выбор монтажа)

---

## 6) WHEN TO CREATE A NEW SOUND/MUSIC SPECIALIST (GATE)
Новый SOUND_MUSIC SPC создаётся только если:
- появляется устойчивый тип задач, не закрытый текущими 11 ролями
- нужен отдельный контракт (например Foley specialist или dialogue edit)
- роль становится постоянной дырой в пайплайне

---

## 7) FAMILY NAV — SPECIALISTS (ORDER IS LAW)
01 — MUSIC SUPERVISOR  
02 — MUSIC PRODUCER  
03 — COMPOSER  
04 — SONGWRITER  
05 — LYRICIST  
06 — ARRANGER  
07 — VOCAL DIRECTOR  
08 — SOUND DESIGNER  
09 — MIX ENGINEER  
10 — MASTERING ENGINEER  
11 — AUDIO QA  

---

## FINAL RULE (LOCK)
Этот README задаёт границы семьи `06_SOUND_MUSIC`.  
Если нет sonic identity, ясности и контроля дрейфа — звук/музыка превращаются в случайный набор треков и ломают восприятие.

--- END.
