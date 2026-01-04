# KNOWLEDGE PRODUCTION ENGINES — Realm
FILE: 00__README__KNOWLEDGE_PRODUCTION_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Realm file for media/knowledge production engines (visual, camera, lighting, generation, editing, audio)

---

## WHAT THIS FAMILY IS

**KNOWLEDGE_PRODUCTION_ENGINES** — это слой “медиапроизводства”.
Он отвечает за то, чтобы любые идеи, сцены, правила мира и смыслы
могли быть **выпущены как визуальные/аудио артефакты**:

- кадры, арты, раскадровки
- стиль и дизайн
- камера и кинематография
- свет
- генерация изображений/видео
- монтаж
- звук и музыка (на уровне синхронизации и дизайна, без композиторской глубины)

---

## WHY IT EXISTS

Потому что “канон” без медиа-пайплайна:
- выглядит хаотично
- теряет стиль
- не масштабируется в выпуск
- ломает атмосферу и узнаваемость

Это семейство делает **конвейер производства**.

---

## INPUT / OUTPUT

### Inputs
- Scene specs (из narrative engines / projects)
- Style targets (genre/style engines)
- Asset constraints (что есть/нет)
- Platform format constraints (параметры выходного материала)

### Outputs
- Visual/audio production specs
- Prompt packs / shot lists / lighting notes
- Generation presets
- Editing rules
- QA gates for media consistency

---

## FAMILY-WIDE CANON TERMS

### MEDIA SPEC
Набор параметров, который достаточно точен, чтобы другой человек/агент мог повторить результат.

### STYLE LOCK
Набор неизменяемых признаков: палитра/контраст/зерно/линзы/ритм/звук.

### SHOT LIST
Список кадров: кто/где/какая камера/какой свет/какой смысл.

### PROMPT PACK
Набор промптов + негативов + параметров генерации + референсов + “do not”.

---

## FAMILY CONTENTS

01 — Visual Composition Engine
02 — Art Style Engine
03 — Camera & Cinematography Engine
04 — Lighting Engine
05 — Image Generation Engine
06 — Video Generation Engine
07 — Editing & Montage Engine
08 — Sound & Music Engine (production-level sync/design, not composition deep-dive)

---

## FAMILY-WIDE VALIDATION

- KP1: Любой артефакт должен ссылаться на сцену/цель (зачем он).
- KP2: Стиль фиксируется и повторяем.
- KP3: Результат воспроизводим по спецификации (если нельзя повторить — значит это не “система”, а случайность).

---
OWNER: Universe Engine
STATUS: FIXED
