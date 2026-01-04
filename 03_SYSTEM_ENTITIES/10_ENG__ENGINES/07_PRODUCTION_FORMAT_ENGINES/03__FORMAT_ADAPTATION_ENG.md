# Format Adaptation Engine
FILE: 03__FORMAT_ADAPTATION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Converts a canonical narrative/scene spec into different output formats (book/series/shorts/youtube/game) via invariants, compression/expansion rules, beat re-mapping, and platform constraints; produces Adaptation Specs, Beat Translation Maps, Core Invariants, and QC Gates to preserve genre contract, meaning, and clarity across mediums

---

## PURPOSE

Одна и та же “история/канон” может жить в разных форматах:
- книга
- сериал/эпизоды
- короткие ролики
- ютуб-лонгформ
- игра

Движок нужен, чтобы:
- не ломать смысл и жанровый контракт при переносе
- уметь сжимать/разворачивать без потери ядра
- учитывать платформенные ограничения (время/внимание/темп)
- дать воспроизводимый стандарт адаптации

---

## NON-GOALS

- не пишет историю вместо Narrative engines
- не режиссирует кадры (это knowledge production)
- не заменяет жанр (Genre engine)
Он делает **перевод** “канона в формат” как процедуру.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Canon scene specs (beats, stakes, arc)
- Genre Bible + blending spec (если есть)
- Tone/Mood locks
- Target platform constraints (duration, pacing)
- Existing shot list (если видеорежим)

### PRODUCES
- ADAPTATION SPEC (AS) — canonical artifact
- CORE INVARIANTS (CI)
- BEAT TRANSLATION MAP (BTM)
- COMPRESSION/EXPANSION RULES (CER)
- FORMAT-SPECIFIC STRUCTURE (FSS)
- FAILSAFE RULES (AFR)
- ADAPTATION QC GATES (AQG)

### DEPENDS_ON
- 07_PRODUCTION_FORMAT_ENGINES/01__GENRE_ENG.md
- 07_PRODUCTION_FORMAT_ENGINES/02__GENRE_BLENDING_ENG.md (if used)
- 02_DOMAIN_NARRATIVE_ENGINES (structure, continuity, meaning)
- 06_GENRE_STYLE_ENGINES (tone/atmosphere)
- 05_EXPRESSION_ENGINES (beats)

### OUTPUT_TARGET
- Feeds:
  - book chapters outline
  - episode breakdown
  - short script boards
  - youtube longform outline
  - game quest/mission flow

---

## CANON TERMS

### CORE INVARIANTS (CI)
То, что нельзя потерять:
- ключевые обещания/пэйоффы
- ключевые решения персонажей
- ключевые факты мира
- смысловые опоры темы
- причинно-следственный скелет

### ADAPTATION MODE
- compress (сжать)
- expand (расширить)
- translate (переложить в другую механику)
- hybrid (смешанный)

### BEAT
Минимальная единица “драматического события” (setup → change → consequence).

### ATTENTION BUDGET
Сколько зритель/читатель выдержит без “оплаты” (hook/payoff).

---

## CORE RULES (CANON)

### FA1 — Invariants first
Сначала фиксируем CI, потом режем/растягиваем.

### FA2 — Genre contract must survive
В любом формате:
- обещания жанра остаются
- payoff не исчезает
- табу соблюдены

### FA3 — Beats are translated, not copied
Одинаковый beat может стать:
- страницей в книге
- сценой в сериале
- 10 сек в shorts
- механикой квеста в игре

### FA4 — Compression must keep causal chain
При сжатии:
- нельзя выкинуть причинность
- если выкинул — должен заменить мостом/маркером

### FA5 — Expansion must not add noise
При расширении:
- нельзя добавлять сцены без функции
- каждый добавленный beat должен:
  - усиливать stakes/персонажа/мир/тему

### FA6 — Platform constraints are law
Если платформа требует:
- hook в первые 3–10 сек
- клифф в конце эпизода
- интерактивную мотивацию
→ это фиксируется как FSS и проверяется AQG.

---

## REQUIRED ARTIFACT A: ADAPTATION SPEC (AS)

### AS SCHEMA (CANON)

Header:
- AS_ID:
- SOURCE_CANON_ID:
- TARGET_FORMAT:
  - book | series | short | youtube_longform | game
- MODE:
  - compress | expand | translate | hybrid
- VERSION:
- STATUS:
  - draft | canon | deprecated

Constraints:
- TARGET LENGTH:
  - pages / minutes / episodes / missions
- ATTENTION BUDGET:
  - hook window, payoff cadence
- CLARITY FLOOR:
- EXPO POLICY:
  - allowed exposition density

Outcome locks:
- GENRE LOCK:
- TONE LOCK:
- ENDING LOCK:
  - closed/open/bittersweet/etc

Rule:
- AS must exist for any non-native format output.

---

## REQUIRED ARTIFACT B: CORE INVARIANTS (CI)

### CI SCHEMA (CANON)

- CI_ID:
- AS_ID:

Invariants list (repeat):
- INVARIANT:
- TYPE:
  - plot fact | character choice | world law | theme anchor | payoff
- WHY IT MATTERS:
- “BREAK COST”:
  - what collapses if removed
- REQUIRED PRESENCE:
  - must be explicit | can be implicit

Rule:
- CI must include at least:
  - 2 plot facts
  - 2 character choices
  - 1 world law
  - 1 theme anchor
  - 1 payoff requirement

---

## REQUIRED ARTIFACT C: BEAT TRANSLATION MAP (BTM)

### BTM SCHEMA (CANON)

- BTM_ID:
- AS_ID:

For each source beat:
- SOURCE BEAT ID:
- SOURCE FUNCTION:
  - setup | escalation | reveal | reversal | climax | resolution
- TARGET UNIT:
  - chapter | scene | short segment | youtube segment | quest step
- TARGET DURATION:
- TRANSLATION METHOD:
  - dialogue | action | montage | mechanic | environmental storytelling
- CLARITY NOTE:
  - what must be understood
- PAYOFF MARKERS:
  - where the beat is paid

Rule:
- If a source beat is removed → must have replacement marker.

---

## REQUIRED ARTIFACT D: COMPRESSION / EXPANSION RULES (CER)

### CER SCHEMA (CANON)

- CER_ID:
- AS_ID:

Compression rules:
- MERGE RULES:
  - which beats can merge
- CUT RULES:
  - what can be cut safely
- BRIDGE RULES:
  - how to preserve causality (1–2 lines, montage, UI, narration)

Expansion rules:
- ADD RULES:
  - what kinds of beats are allowed (world texture, character friction)
- NOISE BAN:
  - what is forbidden (random filler)
- PAYOFF SUPPORT:
  - how expansion strengthens later payoffs

Rule:
- CER prevents “random trimming” and “random filler”.

---

## REQUIRED ARTIFACT E: FORMAT-SPECIFIC STRUCTURE (FSS)

### FSS SCHEMA (CANON)

- FSS_ID:
- AS_ID:

Templates:

#### BOOK
- CHAPTER TARGET:
- POV POLICY:
- EXPO DENSITY:
- DESCRIPTION vs ACTION BALANCE:
- CLIFFHANGER POLICY (optional)

#### SERIES
- EP LENGTH:
- ACT BREAKS:
- COLD OPEN POLICY:
- CLIFFHANGER POLICY:
- RECAP POLICY:

#### SHORT (TikTok/Reels/Shorts)
- HOOK WINDOW (sec):
- PAYOFF WINDOW (sec):
- MAX CONCEPTS PER SHORT:
- TEXT ON SCREEN POLICY:
- LOOP POLICY:
- CTA POLICY (if needed)

#### YOUTUBE LONGFORM
- OPEN LOOP:
- SECTIONING:
- MIDPOINT RESET:
- RETENTION PAYOFF POINTS:
- SUMMARY POLICY:

#### GAME
- PLAYER AGENCY POLICY:
- QUEST LOOP:
- FAILURE/RETRY DESIGN:
- REWARD CADENCE:
- DIEGETIC EXPO RULES:
- CUTSCENE CAP:

Rule:
- FSS is the operational template used by writers/editors.

---

## REQUIRED ARTIFACT F: FAILSAFE RULES (AFR)

### AFR SCHEMA (CANON)

- AFR_ID:
- AS_ID:

Failsafes:
- If clarity drops → add bridge marker (montage/narration/dialogue)
- If genre promise delayed too long → insert micro-payoff
- If stakes feel flat → strengthen consequence beat
- If runtime too long → merge beats per CER merge rules
- If runtime too short → add expansion beats only from allowed list
- If audience confused → reduce concepts per unit

Rule:
- Failsafes act as emergency fixes without breaking CI.

---

## REQUIRED ARTIFACT G: ADAPTATION QC GATES (AQG)

### AQG SCHEMA (CANON)

- AQG_ID:
- AS_ID:

Gates:
1) Invariants gate:
   - CI present and intact
2) Genre gate:
   - promises and taboos respected
3) Causality gate:
   - causal chain preserved or bridged
4) Platform gate:
   - FSS constraints satisfied
5) Clarity gate:
   - no missing knowledge to follow
6) Payoff cadence gate:
   - attention budget respected
7) Noise gate:
   - no filler (for expansion) / no amputations (for compression)

Rule:
- Fail 2+ gates → adaptation must be revised.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- CI not defined
- important beat removed without bridge
- compression makes motivations unclear
- expansion adds scenes with no function
- platform template ignored (no hook in short, no act breaks in series)
- payoff cadence too slow for the platform
- ending type changes without governance

Fix options:
- rewrite CI and rerun BTM
- add bridge markers and clarity beats
- merge beats instead of cutting
- remove filler and replace with functional expansion
- enforce FSS and attention budget points
- apply governance if ending/genre changes

---

## PROCEDURE (HOW TO RUN)

1) Choose target format and mode (compress/expand/translate)
2) Draft AS with constraints and locks
3) Define CI (what cannot be lost)
4) Build BTM (beat-by-beat translation)
5) Define CER (how to cut/merge/bridge or expand safely)
6) Apply FSS template rules
7) Add AFR failsafes
8) Run AQG gates on outline and final output
9) Canonize AS and log changes via governance

---

## QC CHECKLIST (MANDATORY)

- AS exists with target constraints and locks?
- CI lists invariants across plot/character/world/theme/payoff?
- BTM maps beats to target units with translation methods?
- CER defines safe merges/cuts and safe expansions?
- FSS template exists and is followed?
- AFR failsafes exist?
- AQG gates are used?

---

## VALIDATION RULES

- FAV1: Core invariants survive format change.
- FAV2: Causality and motivations remain clear.
- FAV3: Platform constraints are satisfied without breaking canon.
- FAV4: Compression/expansion is functional, not random.

---

OWNER: Universe Engine
LOCK: FIXED
