# SPEECH NATURALIZATION ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/08__SPEECH_NATURALIZATION_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
ENGINE: 08__SPEECH_NATURALIZATION_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.CHAR.SPEECH.NAT.001
OWNER: SYSTEM
ROLE: Transform dialogue intent specs into natural human speech patterns: voice profile, cadence, lexical habits, filler strategy, politeness/aggression modulation, and constraint gates (without writing final scripted lines).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Speech Naturalization Engine created: voice profile schema, cadence model, lexical habits, subtext leakage patterns, and naturalness gates."
- REASON: "Dialogue intent is not enough; characters need distinct, believable speech behavior."
- IMPACT: "Dialogue generation becomes consistent, differentiated, and less 'written'."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.CHAR.SPEECH.NAT.001

---

## 0) PURPOSE (LAW)
Этот движок делает диалог “живым” на уровне **речевого поведения**:
- голосовой профиль персонажа (voice)
- каденс/темп/ритм фраз
- лексические привычки и запрещённые слова/темы
- стратегии пауз/оговорок/уточнений
- как подтекст “протекает” (leakage)
- модуляция речи по стрессу и по отношению к собеседнику

Важно: движок **не пишет финальные реплики**; он задаёт правила, по которым реплики потом будут генерироваться/редактироваться.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- создание сцен/битов (narrative family)
- финальную художественную полировку текста (writing/editing)
- продакшн-исполнение (актёрская речь/микрофон/монтаж) — это production engines
- мировые языки/диалекты как система (world family), но может потреблять constraints

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–18)
- `CORE_IDENTITY`
- `CORE_STATE`
- `CHARACTER_CORE_PASSPORT`
- `CHARACTER_TRAIT_PROFILE`
- `MOTIVATION_DESIRE_STACK` (optional)
- `VALUE_HIERARCHY` (optional)
- `INNER_STATE_MODEL` (optional)
- `STRESS_ESCALATION_LADDER` (optional)
- `RELATIONSHIP_GRAPH` (optional)
- `RELATIONSHIP_CONTRACTS` (optional)
- `DIALOGUE_INTENT_CARDS` (required)
- `SUBTEXT_MAP` (optional)
- `CONVERSATION_TACTICS_CATALOG` (optional)
- `WORLD_LAW_SEEDS` (optional: cultural constraints)
- `LANGUAGE_CONSTRAINTS` (optional: slang limits, taboo words)
- `NATURALNESS_GATES_SPEC` (optional: standard gates if exists)
- `SCENE_BLUEPRINT_SET` (optional)
- `BEAT_MAP` (optional)

### PRODUCES (1–7)
- `VOICE_PROFILE`
- `SPEECH_PATTERN_RULESET`
- `NATURALNESS_GATE_REPORT`

### DEPENDS_ON
- `[03_DOMAIN_CHARACTER_ENGINES/07__DIALOGUE_ENG, 03_DOMAIN_CHARACTER_ENGINES/04__CHARACTER_PSYCHOLOGY_ENG, 03_DOMAIN_CHARACTER_ENGINES/06__RELATIONSHIP_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/SPEECH/`

---

## 3) DEFINITIONS (LOCAL)
- **Voice Profile** — устойчивый “голос” персонажа (лексика/тон/структура).
- **Cadence** — длина фраз, паузы, скорость.
- **Leakage** — как скрытое проявляется наружу (оговорка, уточнение, сарказм).
- **Naturalness Gates** — быстрые проверки “звучит ли как человек”.
- **Style Clamp** — ограничение, чтобы персонажи не говорили одинаково.

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- речевые привычки/паттерны персонажа
- адаптация речи по отношениям и стрессу
- фильтры “не говорить так” (taboo lexicon / forbidden constructions)
- naturalness gates и отчёт

### OUT OF SCOPE (HARD)
- финальные реплики как литературный продукт
- глобальная стилизация жанра (это style engines)
- продакшн-техническая запись/монтаж звука (production)

### COLLISION RULE (ROUTING)
- Если вопрос про “жанровый тон текста” → `06_GENRE_STYLE_ENGINES/*`
- Если вопрос про “монтаж/темп на экране” → `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG`
- Если вопрос про “что говорить и зачем” → `07__DIALOGUE_ENG`

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `VOICE_PROFILE`
**MUST (fields):**
- `character_id`
- `version`
- `baseline_voice` (core)
- `lexicon_rules` (word habits)
- `syntax_rules` (sentence structure)
- `cadence_model`
- `tone_range` (allowed tones)
- `taboo_lexicon[]` (optional)
- `signature_moves[]` (unique markers)
- `do_not_do[]` (anti-voice constraints)
- `open_unknowns[]`
- `scope_notes`

**Baseline voice (minimum):**
- `register` (enum: `FORMAL|NEUTRAL|CASUAL|ROUGH|ACADEMIC|STREET`)
- `directness` (0..100)
- `warmth` (0..100)
- `sarcasm` (0..100)
- `verbosity` (0..100)
- `certainty_style` (enum: `ASSERT|HEDGE|QUESTION|QUALIFY`)
- `metaphor_usage` (0..100)
- `profanity_level` (0..100)
- `honesty_style` (enum: `BLUNT|STRATEGIC|EVASIVE`)

**Lexicon rules (minimum):**
- `preferred_words[]`
- `avoided_words[]`
- `favorite_phrases[]` (optional)
- `filler_strategy` (enum: `NONE|LIGHT|MEDIUM|HEAVY`)
- `filler_examples[]` (optional)
- `domain_terms[]` (optional: jargon they know)

**Syntax rules (minimum):**
- `sentence_length` (enum: `SHORT|MIXED|LONG`)
- `question_rate` (0..100)
- `interrupt_rate` (0..100)
- `self_correction_rate` (0..100)
- `ellipsis_rate` (0..100)

**Cadence model (minimum):**
- `pace` (enum: `SLOW|MEDIUM|FAST`)
- `pause_frequency` (0..100)
- `pause_types[]` (e.g., "thinking pause", "tactical pause")
- `emphasis_style` (enum: `REPEAT|CUT|RISE|UNDERSTATE`)

**Signature move (minimum):**
- `id`
- `marker` (what it looks like)
- `when_used`
- `risk` (optional)

**VALIDATION:**
- voice profile must produce at least 3 distinguishing markers (signature moves or strong lexicon rules)
- do_not_do must include at least one anti-pattern constraint (e.g., “no monologues”, “no perfect sentences”)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/SPEECH/<character_id>/VOICE_PROFILE.md`

---

### B) `SPEECH_PATTERN_RULESET`
**MUST (fields):**
- `character_id`
- `patterns[]`
- `context_modulators[]`
- `stress_modulators[]`
- `subtext_leakage_rules[]`
- `repair_moves[]` (how they recover from mis-speak)
- `checks[]`

**Pattern (minimum):**
- `pattern_id`
- `intent_type` (enum: `REVEAL|THREAT|APOLOGY|TEST|NEGOTIATE|DEFLECT|CHARM|STONEWALL|CONFESS`)
- `default_form` (template-like description; not final text)
- `common_variants[]`
- `what_to_avoid[]`
- `notes`

**Context modulator (minimum):**
- `context` (enum: `ALLY|ENEMY|AUTHORITY|INTIMATE|PUBLIC|PRIVATE`)
- `delta` (changes to baseline_voice fields)
- `notes`

**Stress modulator (minimum):**
- `stress_level_ref` (ladder id or range)
- `delta`
- `failure_modes[]` (e.g., "stutters", "goes silent", "overexplains")
- `notes`

**Subtext leakage rule (minimum):**
- `when` (subtext pattern)
- `leak_signal` (how it leaks)
- `masking_move` (how they cover it)
- `risk` (`LOW|MEDIUM|HIGH`)

**Repair move (minimum):**
- `move_id`
- `trigger` (mistake type)
- `move` (how they correct)
- `cost` (social/psychological)

**VALIDATION:**
- must define at least 5 intent_type patterns
- at least one failure mode under high stress
- context modulators must exist for at least `ALLY` and `ENEMY` (S1 if missing)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/SPEECH/<character_id>/SPEECH_PATTERN_RULESET.md`

---

### C) `NATURALNESS_GATE_REPORT`
**MUST (fields):**
- `character_id`
- `version`
- `gates[]`
- `issues[]`
- `fix_suggestions[]`
- `overall_grade` (enum: `PASS|WARN|FAIL`)
- `notes`

**Gate (minimum):**
- `gate_id`
- `name`
- `pass_condition`
- `fail_condition`
- `severity` (`S0|S1|S2|S3`)

**Recommended gates (baseline set):**
- `G1_ON_THE_NOSE` — too explicit, no hidden goal
- `G2_SAME_VOICE` — indistinguishable from others
- `G3_PERFECT_SENTENCES` — no fillers/repairs, overly written
- `G4_INFO_DUMP` — unnatural exposition
- `G5_NOISE` — too many fillers, incoherent
- `G6_CONTEXT_BLIND` — same tone with enemy/ally
- `G7_STRESS_FLAT` — no stress modulation
- `G8_TABOO_BREACH` — violates taboo lexicon/relationship contracts

**Issue (minimum):**
- `issue_id`
- `gate_id`
- `description`
- `severity`
- `where` (card/pattern reference)

**Fix suggestion (minimum):**
- `issue_id`
- `suggestion`

**VALIDATION:**
- report must include at least 6 gates
- FAIL if any S0 gate fails

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/SPEECH/<character_id>/NATURALNESS_GATE_REPORT.md`

---

## 6) PROCESS (PIPELINE)
1) Read dialogue intent cards and relationship contexts.
2) Build baseline voice from traits + behavior style.
3) Define lexicon/syntax/cadence and signature moves.
4) Build context modulators (ally/enemy/authority/intimate/public).
5) Build stress modulators from ladder + psychology.
6) Define subtext leakage rules + repair moves.
7) Run naturalness gates and emit report.
8) Output voice profile + ruleset.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- taboo breach is unavoidable under default rules (must clamp lexicon)
- voice is not differentiable (no signature markers) (FAIL)
- stress modulation absent while stress ladder exists (FAIL)
- ruleset produces only explicit talk (on-the-nose everywhere)

S1 (HIGH) if:
- context modulators missing for enemy/authority
- repair moves absent (speech too perfect)

S2/S3: quality warnings.

---

## 8) NOTES FOR DOWNSTREAM ENGINES
- Writing/expression can later generate actual lines using intent cards + voice rules.
- Production audio/acting can interpret cadence and stress failure modes.
- Continuity can compare generated speech to voice profile for drift detection.

---

LOCK: OPEN
