# SPC FAMILY REALM — VISUAL SPECIALISTS (CANON)
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/05_VISUAL/00__README_VISUAL_SPECIALISTS.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
DOC_TYPE: README
INDEX_TYPE: FAMILY_REALM
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.REALM.VISUAL.001
OWNER: SYSTEM
ROLE: Family realm definition + boundaries + navigation rules for SPC family `05_VISUAL`

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established VISUAL SPC family realm: responsibilities, boundaries, interfaces, quality rules, and production handoffs."
- REASON: "Need deterministic visual pipeline roles: direction, design, visualization, storyboards, cinematography, and camera movement."
- IMPACT: "Visual production becomes coherent: consistent look, scene clarity, shot logic, and camera grammar."
- CHANGE_ID: UE.CHG.2026-01-09.SPC.REALM.VISUAL.001

---

## 0) PURPOSE (LAW)
Семейство `05_VISUAL` отвечает за визуальную реализацию как систему:
- визуальная режиссура (как выглядит и ощущается визуально)
- продакшн-дизайн (мир/сцены/предметная среда)
- визуализация сцен (перевод текста в видимые композиции)
- сториборд (кадровка, последовательность, ясность)
- операторская работа (свет/линза/кадр как язык)
- движение камеры (грамматика движения и темп)

Цель семьи — сделать визуал **воспроизводимым, ясным и единым**: чтобы любой эпизод/сцена читались визуально и соответствовали направлению.

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
**FAMILY NAME:** VISUAL SPECIALISTS  
**FAMILY PATH:** `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/05_VISUAL/`

### 2.1 Covered domains (what we DO)
- Visual direction (look consistency)
- Production design (space/props/set logic)
- Scene visualization (composition + beats)
- Storyboarding (shot sequence)
- Cinematography (lens/light/framing language)
- Camera movement (movement grammar)

### 2.2 Hard boundaries (what we DO NOT do)
- Не пишем сюжет/диалоги (это `02_NARRATIVE`), мы исполняем визуально.
- Не создаём канон мира (это `04_WORLD` + lore/governance), но соблюдаем.
- Не делаем звук/музыку (это `06_SOUND_MUSIC` и ENG 09).
- Не делаем монтаж как отдельную область (это production/`08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md`).
- Не делаем финальную генерацию изображений/видео как инструмент (это `08_KNOWLEDGE_PRODUCTION_ENGINES/*`), но задаём требования.

---

## 3) DEFAULT OUTPUT PHILOSOPHY
**Default mindset:** INTENT → VISUAL RULES → SHOTS → CLARITY  
**Primary quality priority:** clarity → consistency → emotion support  
**Default outputs:**
- visual bible snippets (правила стиля/направления)
- scene visualization sheets (композиция/ключевые кадры)
- storyboard sequences
- shotlists + camera grammar notes

---

## 4) INTERFACES (SYSTEM LINKS)
### 4.1 ENG (Engines) — typical support
- `08_KNOWLEDGE_PRODUCTION_ENGINES/01__VISUAL_COMPOSITION_ENG.md`
- `08_KNOWLEDGE_PRODUCTION_ENGINES/03__CAMERA_CINEMATOGRAPHY_ENG.md`
- `08_KNOWLEDGE_PRODUCTION_ENGINES/04__LIGHTING_ENG.md`
- `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md` (как ограничения темпа)

### 4.2 ORC — typical usage
ORC вызывает VISUAL SPC когда нужно:
- зафиксировать визуальное направление/правила (Visual Director)
- построить среду сцены (Production Designer)
- превратить текст в видимые композиции (Scene Visualization Specialist)
- сделать кадрировку (Storyboard Artist)
- определить операторский язык (Cinematographer)
- определить движения камеры (Camera Movement Specialist)

### 4.3 QA / VAL gates
Типовые гейты:
- visual clarity sanity (сцена читается?)
- consistency sanity (стиль не дрейфует)
- continuity sanity (пространство/позиции не ломаются)
- production feasibility (если применимо)

---

## 5) FAMILY STANDARDS (MANDATORY RULES)
### 5.1 Anti-overlap (role separation)
- Visual Director: владелец “как выглядит” (rules + consistency).
- Production Designer: владелец среды/сеттинга кадра (props/space).
- Scene Visualization Specialist: перевод сцены в композицию и ключевые кадры.
- Storyboard Artist: последовательность кадров и ясность переходов.
- Cinematographer: линзы/свет/кадр как язык.
- Camera Movement Specialist: движения камеры и темп движения.

### 5.2 Visual clarity law
Любая визуальная сцена должна отвечать:
- где мы (пространство)
- кто где (блокинг)
- что происходит (action beats)
- что важно (focus)
- что изменилось (state change визуально)

### 5.3 Consistency law
- Всё должно быть совместимо с Visual Director rules.
- Любые отклонения маркируются как intentional exception.

---

## 6) WHEN TO CREATE A NEW VISUAL SPECIALIST (GATE)
Новый VISUAL SPC создаётся только если:
- появляется устойчивый тип задач, не закрытый текущими 6 ролями
- нужен отдельный контракт (например VFX pipeline)
- роль становится постоянной дырой в производстве

---

## 7) FAMILY NAV — SPECIALISTS (ORDER IS LAW)
01 — VISUAL DIRECTOR  
02 — PRODUCTION DESIGNER  
03 — SCENE VISUALIZATION SPECIALIST  
04 — STORYBOARD ARTIST  
05 — CINEMATOGRAPHER  
06 — CAMERA MOVEMENT SPECIALIST  

---

## FINAL RULE (LOCK)
Этот README задаёт границы семьи `05_VISUAL`.  
Если сцена визуально не отвечает “где/кто/что/что важно/что изменилось” — визуальная реализация считается неготовой.

--- END.
