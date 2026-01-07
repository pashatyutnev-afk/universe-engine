# NATURALNESS GATES STANDARD (SoT)
FILE: 02_STANDARDS/01_SPECIFICATIONS/06__NATURALNESS_GATES_STANDARD.md

SCOPE: Universe Engine / Standards
LEVEL: L0
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Стандарт естественности: правила “не палиться как ИИ”, плюс правила поведения/речи по классу существа.

REFERENCES:
- Marking SoT: `02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md`
- QA Rules: `03_SYSTEM_ENTITIES/60_QA__QUALITY/01__RULES__QA.md`
- Scene 4Track: `02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md`

---

## 0) PURPOSE
Naturalness Gates — это “фильтр качества”, который:
- блокирует “ИИ-сигнатуры” в тексте/речи/описаниях
- следит за правдоподобием поведения и движений
- учитывает CLASS существа (человек/робот/животное/дух...)

---

## 1) NATURALNESS PROFILE (MANDATORY FOR SCENE/CHARACTER OUTPUTS)
Любой результат сцены/диалогов/поведения должен иметь профиль:

NAT_PROFILE:
  ENTITY_CLASS: <HUMAN|ROBOT|ANIMAL|SPIRIT|ALIEN|OTHER>
  STYLE_MODE: <REALISTIC|STYLIZED|MYTHIC|CARTOON>
  LANGUAGE_MODE: <NATURAL|FORMAL|ROUGH|POETIC|TECHNICAL>
  LIMITS:
    MAX_EXPLAINING: <LOW|MID|HIGH>
    MAX_SYMMETRY: <LOW|MID|HIGH>
    MAX_GENERICNESS: <LOW|MID|HIGH>
  NOTES: ""

Если NAT_PROFILE отсутствует — QA выставляет S1 (или S0 если это финальный OUT).

---

## 2) AI TRACE RED FLAGS (CANON LIST)
Если встречается — QA обязателен ISSUE.

### TEXT/SPEECH RED FLAGS
- RF_TXT_01: “слишком правильная” речь без живых ошибок/ритма
- RF_TXT_02: повтор одинаковых конструкций / параллельная симметрия
- RF_TXT_03: общие фразы без конкретики (genericness)
- RF_TXT_04: сверх-объяснение (много “пояснений” вместо действия)
- RF_TXT_05: резкие смены стиля без причины
- RF_TXT_06: шаблонные “канцелярские” связки в художественном тексте

### VISUAL/DESCRIPTION RED FLAGS
- RF_VIS_01: “перечень” деталей без фокуса/камеры
- RF_VIS_02: всё одинаково важное (нет foreground/background)
- RF_VIS_03: невозможная физика без объяснения мира (если STYLE_MODE=REALISTIC)

### MOTION/BEHAVIOR RED FLAGS
- RF_MOT_01: движения описаны как “робот” при ENTITY_CLASS=HUMAN
- RF_MOT_02: отсутствие микро-движений, веса, инерции (при REALISTIC)
- RF_MOT_03: одинаковый темп/ритм на всём протяжении

### SOUND RED FLAGS
- RF_SND_01: музыка “везде”, нет тишины/дыхания сцены
- RF_SND_02: эффекты не соответствуют материалам/пространству

---

## 3) CLASS BEHAVIOR RULES (CANON)
### HUMAN
- допускаются: оговорки, микро-паузы, эмоциональные сдвиги
- запрещено (S1/S0): идеально вылизанная речь без жизни, “лекционный” тон без причины

### ROBOT
- допускается: ровность/точность, механические паттерны
- запрещено: чрезмерная человечность без сюжетного обоснования (если не задано)

### ANIMAL
- речь: обычно NONE (если не антропоморф)
- поведение: реактивность, инстинкты, внимательность к среде
- запрещено: “человеческая логика” без пояснения

### SPIRIT / GHOST
- допускается: странность, нелинейность, символизм
- запрещено: бытовая физика как у человека, если не задано

OTHER
- правила обязаны быть описаны локально в сцене/персонаже

---

## 4) GATE LEVELS (PASS/FAIL WITH SEVERITY)
QA применяет Naturalness Gate так:

- S0 FAIL: явное “палево ИИ” или ломает CLASS/STYLE_MODE
- S1 FAIL: заметно большинству, ухудшает продукт
- S2 PASS WITH WARN: можно выпускать черновик
- S3 PASS NOTE: улучшение

---

## 5) QA ISSUE TEMPLATE (NAT)
ISSUE:
  CODE: <RF_TXT_01 ...>
  SEVERITY: <S0..S3>
  MESSAGE: "<что палится>"
  FIX_SUGGESTION: "<как сделать естественней>"

---

## 6) FINAL LAW
> Naturalness — это не вкусовщина. Это gate. Если gate FAIL — выпуск запрещён.

---
END.
