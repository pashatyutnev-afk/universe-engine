# 22__PIPE_MUSIC_IDENTITY

DOC_TYPE: PIPE
DOMAIN: MUSIC
PIPE_ID: MUS.IDENTITY
VERSION: 1.4.0
UPDATED: 2026-02-09

---

## PURPOSE
Собрать идентику трека: нейминг, роли, метаданные, позиционирование и “право на релиз”.
Нужно, чтобы система не путалась в названиях, не давала коллизий и могла собирать релиз-пак.

---

## INPUTS
- TASK_TEXT
- BRAND CONTEXT (если есть)
- STYLE_PROFILE (из 20__PIPE_MUSIC_TRACK)

---

## OUTPUTS
- IDENTITY_TOKEN (title candidates, alias, short tag)
- METADATA_TOKEN (genre tags, mood tags, bpm, language, vocal)
- NAMING_POLICY (правила на названия/серии)
- CREDITS_TOKEN (если нужно)

---

## ENTITY MAP
ORC:
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/16__MUS__IDENTITY_BUILD__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/15__MUS__METADATA_FACTORY__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/18__MUS__RELEASE_ASSEMBLER__ORC__ENT.md

CTL:
- UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/13__MUS__CREDITS_METADATA_POLICY__CTL__ENT.md
- UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/04__MUS__RELEASE_VARIANTS__CTL__ENT.md

VAL:
- UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/07__MUS__NAMING_COLLISION__VAL__ENT.md
- UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/09__MUS__CREDITS_RIGHTS__VAL__ENT.md

---

## STAGES
I0 TITLE POOL
- ORC: Identity Build → 5–12 названий (RU), короткий shout-tag (0–1s), варианты “жёстче/мягче”

I1 METADATA
- ORC: Metadata Factory → BPM, feel, tags, vocal, duration target

I2 POLICY
- CTL: Credits/Metadata Policy + Release Variants → правила для релиза/вариантов

I3 VALIDATION
- VAL: Naming Collision → PASS/FAIL
- VAL: Credits Rights → PASS/FAIL (если затрагиваем авторство/сэмплы/рефы)

---

## GATES
- Название произносится и не ломает бренд
- Нет коллизии в каталоге
- Метаданные достаточны для релиза
