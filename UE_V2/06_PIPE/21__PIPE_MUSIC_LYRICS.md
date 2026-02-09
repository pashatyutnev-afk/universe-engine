# 21__PIPE_MUSIC_LYRICS

DOC_TYPE: PIPE
DOMAIN: MUSIC
PIPE_ID: MUS.LYRICS
VERSION: 1.4.0
UPDATED: 2026-02-09

---

## PURPOSE
Сделать текст (RU) с мощным хуком/припевом, плотными образами и управляемым тоном.
Возвращает несколько вариантов для последующего скоринга/синтеза.

---

## INPUTS
- TASK_TEXT
- STYLE_PROFILE (из 20__PIPE_MUSIC_TRACK)
- HOOK_POOL (если уже есть) либо запросить HOOK_FORGE
- CONSTRAINTS (structure, duration, language)

---

## OUTPUTS
- LYRICS_VARIANTS (v1..vN)
- ALT_LINES (по секциям)
- STORY_BEATS
- LYRICS_FINAL_CANDIDATE

---

## ENTITY MAP
ORC:
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/05__MUS__LYRIC_BRIEF_FACTORY__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/06__MUS__LYRIC_DRAFTER__ORC__ENT.md
- UE_V2/03_ENT/30_ORC_ENT/03_MUSIC_ORC_ENT/07__MUS__LYRIC_EDITOR__ORC__ENT.md

CTL:
- UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/11__MUS__CTL__TONE_AND_ETHOS__CTL__ENT.md
- UE_V2/03_ENT/40_CTL_ENT/10_MUSIC_CONTROLLERS_CTL_ENT/12__MUS__CTL__FLOW_AND_PRONUNCIATION__CTL__ENT.md

VAL:
- UE_V2/03_ENT/50_VAL_ENT/10_MUSIC_VAL/11__MUS__VAL__SCORE_RUBRIC__VAL__ENT.md

QA:
- UE_V2/03_ENT/60_QA_ENT/10_MUSIC_QA/11__MUS__QA__LYRICS_COMPLIANCE__QA__ENT.md

---

## STAGES
L0 BRIEF
- ORC: Lyric Brief Factory → BRIEF_TOKEN (сюжет/образы/лексика/запреты)

L1 DRAFT (3–6 вариантов)
- ORC: Lyric Drafter → LYRICS_VARIANTS

L2 EDIT (смысл + рифма + плотность)
- ORC: Lyric Editor → версии с сильными образами и “крючками”

L3 CONTROL
- CTL: Tone/Ethos (уважение/поддержка/границы мата)
- CTL: Flow/Pronunciation (слоги, ударения под BPM/half-time)

L4 QA + SCORE
- QA: Lyrics Compliance → PASS/FAIL + правки
- VAL: Score Rubric → выбрать топ-1 и топ-3 для синтеза

---

## GATES
- Chorus короткий и запоминающийся
- Ритм читается под 94 BPM half-time
- Без запрещённого контента
