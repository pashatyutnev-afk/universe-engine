# 15__VARIANT_POLICY_CTL

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: CTL
UID: UE.V2.CTL.MUSIC.VARIANT_POLICY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Политика генерации вариантов (A/B/C/…) для трека/хука/текста: чем отличаются, как не делать “косметику”.

---

## [M] INTENT
Сделать варианты реально полезными: каждый вариант должен отличаться по 1–2 осям, а не “почти то же самое”.

---

## [M] OUTPUTS
- OPTIONS_TOKEN (A–E)
- SCORE_TOKEN (optional): если включен скоринг

---

## [M] VARIATION_AXES (MUSIC)
Можно варьировать (1–2 оси на вариант):
- AX1: Rhythm (pattern / syncopation / swing)
- AX2: Melody (motive shape / intervals / contour)
- AX3: Harmony (tension / resolution / chord color)
- AX4: Energy (density / drop impact / dynamics)
- AX5: Sound (lead timbre / bass character / drum kit)
- AX6: Arrangement (hook placement / length / transitions)
- AX7: UGC/Hook framing (call/response, “earworm” tactic)
- AX8: Lyrics (if any): imagery / rhyme / cadence

---

## [M] VARIANT RULES
1) Вариант обязан явно указать: какие AX изменены.
2) Запрещены “псевдо-варианты”: если отличия не слышны/не ощущаются → REWORK.
3) Максимум 5 вариантов за шаг (см. STEP_BUDGET_CTL).
4) Варианты должны быть взаимно различимы и пригодны к сравнению.
5) Должен быть дефолт (если пользователь не выбирает) — ORC берёт лучший по QA/score.

---

## [M] RECOMMENDED SETS (DEFAULT)
HOOK:
- A: rhythm-first
- B: melody-first
- C: contrast-first (pause + impact)
- D: timbre-first
- E: ugc-first (repeatable snippet)

TRACK:
- A: aggressive / dense
- B: cleaner / punchy
- C: wider / atmospheric
- D: minimal / groove
- E: hybrid / twist

---

## [M] GATES
PASS если:
- варианты различимы и описаны осями
REWORK если:
- варианты косметические или >5
