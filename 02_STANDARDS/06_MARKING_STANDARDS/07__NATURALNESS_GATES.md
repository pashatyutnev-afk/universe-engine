# NATURALNESS GATES — STANDARD
FILE: 02_STANDARDS/06_MARKING_STANDARDS/07__NATURALNESS_GATES.md

SCOPE: Universe Engine / Quality Gates
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Стандарт “естественности” (правдоподобие формы/движения/речи/стиля) с PASS/FAIL форматом.

SOURCE OF TRUTH:
- Gate-набор, профили формы, формат отчёта — здесь.

---

## 0) CORE LAW
- Gates применяются к сценам/шотам перед фиксацией в CANON.
- Gates завязаны на FORM_PROFILE сущности (BIO/MECH/ETHR/HYBRID).
- Gate FAIL оформляется как FIX с PRIORITY.

---

## 1) FORM_PROFILE (canonical)
- BIO — биология (человек/животное)
- MECH — механика (робот/дрон/техника)
- ETHR — эфирное (призрак/энергия)
- HYBRID — смесь (обязано быть описано)

---

## 2) GATES (minimum set)
- FORM_GATE — допустимые признаки носителя (что “может быть”)
- MOTION_GATE — контакт/инерция/локомоция/масса
- SPEECH_GATE — речь/лексика/манера (или N/A)
- STYLE_GATE — стиль/тон/детализация в рамках жанра/сцены

---

## 3) REPORT FORMAT (canonical YAML block)

NATURALNESS_GATES:
  TARGET:
    SCOPE: "SCENE|SHOT|CHARACTER|ASSET"
    ID: "<ID>"
  FORM_PROFILE: "BIO|MECH|ETHR|HYBRID"

  FORM_GATE: "PASS|FAIL"
  MOTION_GATE: "PASS|FAIL"
  SPEECH_GATE: "PASS|FAIL|N/A"
  STYLE_GATE: "PASS|FAIL"

  FAILS:
    - GATE: "MOTION_GATE"
      CODE: "NO_GROUND_CONTACT"
      PRIORITY: "S1"
      NOTE: "ходьба без контакта/следа"
      FIX_OWNER: "<SPC or ENG>"
4) S0 FAIL CODES (минимальный список)
FORM_IMPOSSIBLE — признаки формы против профиля без объяснения

MOTION_PHYSICS_BREAK — физика полностью ломается без правила мира

STYLE_CONTRACT_BREAK — стиль ломает договор сцены/жанра

5) QUICK RULES (по профилям)
BIO
контакт с поверхностью обязателен при ходьбе

дыхание/усталость допустимы

MECH
нет “человеческой” дыхалки/микромимики без причины

механическая инерция/звук допускаются и желательно консистентны

ETHR
физический контакт только если есть правило/способ

аномальная траектория допустима, но должна быть стабильна

END.