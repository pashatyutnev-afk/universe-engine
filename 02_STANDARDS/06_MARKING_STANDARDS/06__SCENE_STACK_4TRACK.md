# SCENE STACK — 4TRACK STANDARD
FILE: 02_STANDARDS/06_MARKING_STANDARDS/06__SCENE_STACK_4TRACK.md

SCOPE: Universe Engine / Production Scene System
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Канонический формат “DAW-сцены” (Scene Stack): 4 дорожки + синхронизация + связи.

SOURCE OF TRUTH:
- Определение дорожек, формат записей, обязательные поля — здесь.

---

## 0) CORE LAW
- Каждая сцена (ENT:SCENE) обязана иметь соответствующий артефакт SCENE_STACK.
- SCENE_STACK — это не “описание сцены”, а “таймлайновая партитура” (как многодорожка).
- Minimum 4 tracks обязателен всегда.

---

## 1) REQUIRED TRACKS (MINIMUM)
- A_FOCUS — главный фокус (персонаж/объект/ключевое действие)
- B_BG_LIFE — фоновые сущности и “жизнь”
- C_ENV — среда (погода, свет, вода, шум мира, природа, физика)
- D_AUDIO — звук (реплики, шумы, музыка, ключевые cues)

Доп. дорожки разрешены, но не заменяют 4 минимальные.

---

## 2) REQUIRED HEADER FIELDS (SCENE_STACK DOC)
SCENE_STACK документ обязан содержать:
- ID: `ART:SCENE_STACK:<scene_key>:<scope>:vNN`
- SCENE_ID: `<ENT:SCENE:...>`
- PACK_ID: `<ENT:PACK:...>` или `NONE`
- DURATION: `MM:SS.mmm`
- GRID: `seconds` или `fps:<N>`
- ANCHORS: список якорей (минимум 2: START/END)

---

## 3) ANCHORS (canonical)
Формат:

ANCHORS:
  - AT: "00:00.000"
    TAG: "START"
    NOTE: ""
  - AT: "00:12.500"
    TAG: "TURN"
    NOTE: "поворот/событие"
  - AT: "00:24.000"
    TAG: "END"
    NOTE: ""
4) TRACK ENTRY FORMAT (canonical)
Каждая запись:

TIME RANGE: [MM:SS.mmm–MM:SS.mmm]

ACTION: коротко что происходит

LINKS (optional): XREFS на сущности/артефакты

Рекомендуемый формат строки:
[00:02.000–00:08.500] <action> | XREFS: [<ID>, <ID>]

5) LINKING RULES
5.1 Scene → Stack
В документе ENT:SCENE обязательно:

STACK_REF: <ART:SCENE_STACK...>

5.2 Stack → Entities
SCENE_STACK должен ссылаться на ключевые сущности через XREFS (не DEPENDS), если это не сборочная зависимость.

6) STORAGE RULE
Черновики: WORK

Канон: OUTPUT_TARGET
Версии: v01, v02…

7) OPTIONAL EXTENSIONS (добавочные дорожки)
E_MOTION (движения/анимация)

F_CAMERA_EDIT (камера/монтаж)

G_FX (VFX/частицы/магия)

END.