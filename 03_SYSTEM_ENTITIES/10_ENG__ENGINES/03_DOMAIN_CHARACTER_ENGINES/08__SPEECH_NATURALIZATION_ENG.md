# Speech Naturalization Engine
FILE: 08__SPEECH_NATURALIZATION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Converts structured dialogue intent into natural spoken language while preserving voice, subtext, tactics, and relationship state; defines natural speech patterns, micro-errors, interruptions, and rhythm controls + QC gates to avoid over-randomization

---

## PURPOSE

Этот движок делает речь “живой”.
Чтобы реплики:
- звучали как разговор, а не как текст автора
- сохраняли смысл (job) и тактику
- сохраняли голос персонажа (Dialogue Spec)
- отражали отношения (trust/power/intimacy)

---

## NON-GOALS

- не меняет смысл сцены и цели реплик
- не превращает речь в кашу “паразитов”
- не заменяет диалоговый движок (Dialogue engine)
Он **упаковывает** диалог в естественную форму.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Dialogue Spec (DS)
- Subtext Map (SMAP)
- Relationship state (RM/RLSL)
- Psychology Profile (PP) (optional for stress speech)

### PRODUCES
- NATURAL SPEECH RULESET (NSR) — canonical artifact
- VOICE REALISM LAYERS (pause/interrupt/error templates)
- SCENE SPEECH PASS checklist (for rewrite passes)
- “CLEAN vs RAW” policy per project

### DEPENDS_ON
- 03_DOMAIN_CHARACTER_ENGINES/07__DIALOGUE_ENG.md

### OUTPUT_TARGET
- Writer pass / script pass
- Audio performance (if voiced)
- Editing rhythm cues (optional)

---

## CANON TERMS

### NATURALIZATION PASS
Перепаковка реплик, не меняя их “job”.

### LINE JOB
То, что реплика делает (из DS/SMAP).

### SPEECH NOISE
Контролируемый шум:
- паузы
- обрывы
- самопоправки
- недосказанность

### CLARITY FLOOR
Минимум ясности, ниже которого диалог становится нечитабельным.

---

## NATURAL SPEECH TOOLBOX

### A) MICRO-STRUCTURES (SAFE)
- contractions / сокращения
- ellipsis / недоговор
- self-correction (“не… в смысле…”)
- filler word (редко, сигнально)
- short backchannels (“угу”, “да”, “понял”)
- topic jump (если стресс/избегание)

### B) INTERRUPTIONS
- cut-in to seize power
- cut-in to stop emotion
- cut-in to redirect topic
Rule:
- interruption maps to power state (from RM/RLSL).

### C) RHYTHM CONTROL
- short lines under pressure
- longer lines when controlling/performing
- silence as tactic

### D) EMOTION LEAKS
- “лишнее слово”
- неправильный тон
- внезапная грубость
- нервный юмор

---

## REQUIRED ARTIFACT: NATURAL SPEECH RULESET (NSR)

### NSR SCHEMA (CANON)

Header:
- NSR_ID:
- PROJECT/SCOPE:
- VERSION:
- STATUS:
- CLARITY FLOOR:
  - high | medium | low
- STYLE MODE:
  - clean | balanced | raw

Global Rules:
- PRESERVE LINE JOB:
  - mandatory yes
- MAX NOISE PER LINE:
  - low | medium | high
- MAX FILLERS RATE:
  - none | rare | controlled
- SWEAR/SLANG POLICY (optional):
  - allowed | contextual | forbidden
- INTERRUPTION RATE:
  - low | medium | high
- SILENCE POLICY:
  - where silence is used

Per Character Overrides (repeat):
- CHARACTER_ID:
- NATURALIZATION LEVEL:
  - low | medium | high
- PREFERRED STRUCTURES:
  - ellipsis, self-correct, backchannels, etc.
- FORBIDDEN STRUCTURES:
  - e.g., no filler words, no slang
- STRESS SPEECH SHIFT:
  - what changes under stress
- POWER SPEECH SHIFT:
  - how they speak when dominating vs losing

Scene Pass Checklist:
- SCENE_ID:
- CLARITY FLOOR TARGET:
- KEY LINES (must remain clean):
  - list of beats/lines
- ALLOWED NOISE ZONES:
  - where we can go messy
- INTERRUPTION POINTS:
  - who interrupts whom and why
- SUBTEXT LEAKS:
  - what must leak unintentionally

---

## NATURALIZATION RULES (CANON)

### SN1 — Preserve line job
Нельзя менять смысл/цель реплики.
Можно менять форму.

### SN2 — Noise is purposeful
Шум всегда отражает:
- стресс
- власть
- избегание
- эмоциональную утечку
Если шум просто “для реализма” — это мусор.

### SN3 — Clarity floor respected
Если зритель перестал понимать, что происходит — fail.
Особенно на:
- поворотах сюжета
- reveal
- важных обещаниях/клятвах

### SN4 — Character consistency
“Живая речь” тоже должна быть узнаваема.
У каждого персонажа есть:
- 1–3 любимых структуры
- 1–2 запретных структуры

### SN5 — Interruption maps to power
Если персонаж без власти постоянно перебивает — это должно быть:
- intentional (character trait)
- или должно вызывать последствия.

### SN6 — Raw mode is localized
Если включаем “raw” речь, она локальная:
- конкретная сцена
- конкретное состояние
Иначе проект становится неряшливым.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- смысл сцены стал менее понятен после pass
- все персонажи начали говорить одинаково “естественно”
- слишком много filler/паразитов
- слишком много многоточий (визуальный шум)
- interrupt rate не соответствует power state
- важные линии потеряли чистоту

Fix options:
- вернуть clean форму ключевых линий
- уменьшить noise rate
- закрепить per-character structures
- переместить raw только в “allowed noise zones”
- выровнять перебивания по RM/RLSL

---

## PROCEDURE (HOW TO RUN)

1) Take DS + SMAP and mark:
   - key lines (must stay clear)
   - noise zones (allowed)
2) Apply per-character overrides
3) Add minimal micro-structures:
   - ellipsis / self-correct / backchannels
4) Add interruptions aligned with power state
5) Add stress shifts where PP indicates
6) Run clarity check (read out loud test)
7) Lock NSR for scope

---

## QC CHECKLIST (MANDATORY)

- did any line change job? (must be NO)
- are key lines still clean and readable?
- do characters still sound distinct?
- noise rate within max?
- interruptions match relationship power?
- did subtext leaks remain intact?

---

## VALIDATION RULES

- SNV1: NSR exists with clarity floor + mode + character overrides.
- SNV2: Key line jobs preserved after pass.
- SNV3: Natural speech improves realism without reducing comprehension.
- SNV4: Dialogue uniqueness between characters is maintained.

---

OWNER: Universe Engine
LOCK: FIXED
