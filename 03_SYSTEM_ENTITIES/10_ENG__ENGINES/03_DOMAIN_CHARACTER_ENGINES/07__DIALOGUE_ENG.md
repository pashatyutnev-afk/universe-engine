# DIALOGUE ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/07__DIALOGUE_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
ENGINE: 07__DIALOGUE_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.CHAR.DIALOGUE.001
OWNER: SYSTEM
ROLE: Produce deterministic dialogue intent specs: what must be communicated, what is hidden, subtext goals, conversational tactics, and constraint rules (NOT final literary dialogue).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Dialogue Engine created: dialogue intent cards, subtext map, tactics catalog, and dialogue constraint rules."
- REASON: "Scenes need dialogue as a functional system (intent/subtext), not as arbitrary lines."
- IMPACT: "Production and writing can generate actual lines consistently from intent specs."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.CHAR.DIALOGUE.001

---

## 0) PURPOSE (LAW)
Этот движок формирует **диалог как функцию**, а не как литературу:
- что персонаж хочет добиться разговором (goal)
- что он должен сообщить явно (overt content)
- что он скрывает/искажает (concealment)
- какой подтекст (subtext) и тактики используются
- какие ограничения накладывают отношения/мораль/психология
- “диалоговые события” (reveal, threat, apology) как intent-единицы

Выход — спецификация, пригодная для генерации реплик позже.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- финальные реплики/стиль писательства/ритм фраз как текст (это уже expression/production/writing stage)
- естественность речи/разговорность (это `08__SPEECH_NATURALIZATION_ENG`)
- сценическое проектирование целиком (narrative scenes engine)
- монтаж/актёрскую игру (production)
- мировые лингвистические системы (world family; сюда можно подать constraints)

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–16)
- `CORE_IDENTITY`
- `CORE_STATE`
- `CHARACTER_CORE_PASSPORT`
- `CHARACTER_INVARIANTS`
- `CHARACTER_TRAIT_PROFILE`
- `MOTIVATION_DESIRE_STACK`
- `VALUE_HIERARCHY` (optional)
- `MORAL_BOUNDARY_MAP` (optional)
- `INNER_STATE_MODEL` (optional)
- `STRESS_ESCALATION_LADDER` (optional)
- `DECISION_POLICY_MODEL` (optional)
- `RELATIONSHIP_GRAPH` (optional but recommended)
- `RELATIONSHIP_CONTRACTS` (optional)
- `RELATIONSHIP_SHIFT_RULESET` (optional)
- `SCENE_BLUEPRINT_SET` (optional; to bind dialogue to scene goals)
- `BEAT_MAP` (optional; for reveal alignment)

### PRODUCES (1–7)
- `DIALOGUE_INTENT_CARDS`
- `SUBTEXT_MAP`
- `CONVERSATION_TACTICS_CATALOG`

### DEPENDS_ON
- `[03_DOMAIN_CHARACTER_ENGINES/05__CHARACTER_BEHAVIOR_ENG, 03_DOMAIN_CHARACTER_ENGINES/06__RELATIONSHIP_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/DIALOGUE/`

---

## 3) DEFINITIONS (LOCAL)
- **Dialogue Intent Card** — карточка намерения диалога (цель, явное, скрытое, тактика, исход).
- **Overt Content** — что говорится прямо.
- **Subtext** — что на самом деле пытаются сделать/избежать под словами.
- **Tactic** — инструмент разговора (deflect, charm, threaten, confess, test).
- **Turn** — момент изменения в разговоре (truth, power shift, commitment).

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- диалоговые цели и функции (intent)
- правила тактик (что этот персонаж обычно делает в разговоре)
- subtext и concealment (что скрывается)
- ограничения от морали/отношений/психики
- “повороты” диалога (turns) как функциональные события

### OUT OF SCOPE (HARD)
- финальные реплики как художественный текст
- “разговорность/натуральность” как исполнение (это speech naturalization)
- постановка актёрской игры/пауз/интонаций (production)

### COLLISION RULE (ROUTING)
- Если вопрос “как звучит/насколько живо/естественно” → `08__SPEECH_NATURALIZATION_ENG`
- Если вопрос “какой смысл/тема/символы” → narrative theme/style engines
- Если вопрос “какой монтаж/паузы/ритм реплик на экране” → production

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `DIALOGUE_INTENT_CARDS`
**MUST (fields):**
- `character_id`
- `version`
- `cards[]` (list)
- `rules[]` (dialogue constraints)
- `open_unknowns[]`
- `scope_notes`

**Card (minimum):**
- `card_id`
- `counterpart_ids[]` (who is talked to)
- `context_ref` (optional: scene_id/beat_id)
- `goal` (what the speaker wants)
- `overt_message` (what is said explicitly)
- `hidden_goal` (what is actually sought/avoided)
- `subtext` (short)
- `tactics[]` (tactic ids)
- `red_lines[]` (what they will not say/do; from moral boundaries)
- `triggered_by` (optional: stress level / relationship variable threshold)
- `turn` (optional; see Turn schema)
- `success_condition`
- `failure_condition`
- `notes`

**Turn (minimum):**
- `turn_type` (enum: `REVEAL|THREAT|APOLOGY|COMMITMENT|DEFLECTION_BREAK|POWER_SHIFT|CONFESSION|TEST`)
- `what_changes` (short)
- `stakes_delta` (`UP|DOWN|SHIFT|NONE`)

**Rules (minimum):**
- `rule_id`
- `rule_text`
- `strength` (`HARD|SOFT`)
- `why` (short)

**VALIDATION:**
- each card must have goal + overt_message + hidden_goal
- red_lines must be consistent with moral boundaries/invariants
- if a card includes `REVEAL`, it must align with beat/reveal plan if those exist (else open_unknown)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/DIALOGUE/<character_id>/DIALOGUE_INTENT_CARDS.md`

---

### B) `SUBTEXT_MAP`
**MUST (fields):**
- `character_id`
- `patterns[]`
- `avoidances[]`
- `tells[]` (optional: how subtext leaks)
- `stress_shifts[]`
- `open_unknowns[]`

**Pattern (minimum):**
- `pattern_id`
- `when` (situation/relationship context)
- `subtext_goal` (what they do under the surface)
- `cover_story` (what they claim)
- `typical_tactics[]`
- `risk` (`LOW|MEDIUM|HIGH`)

**Avoidance (minimum):**
- `avoid_id`
- `topic` (what they avoid)
- `why` (fear/value)
- `deflection_tactics[]`

**Stress shift (minimum):**
- `stress_level_ref`
- `subtext_change` (how it changes)
- `tactic_shift` (what tactics appear/disappear)

**VALIDATION:**
- at least one avoidance topic for non-trivial characters (S2 warning if none)
- stress shifts must not contradict psychology ladder if present

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/DIALOGUE/<character_id>/SUBTEXT_MAP.md`

---

### C) `CONVERSATION_TACTICS_CATALOG`
**MUST (fields):**
- `catalog_id`
- `tactics[]`
- `usage_rules[]`
- `anti_patterns[]`
- `checks[]`

**Tactic (minimum):**
- `tactic_id`
- `name` (enum-like)
- `definition`
- `best_for` (goals/contexts)
- `risks`
- `signals` (how it manifests)
- `counter_tactics` (what breaks it)

**Usage rule (minimum):**
- `rule_id`
- `rule_text`
- `strength` (`HARD|SOFT`)

**Anti-pattern (minimum):**
- `id`
- `name`
- `symptom`
- `why_bad`
- `fix` (short)

**VALIDATION:**
- catalog must include at least:
  - `DEFLECT`, `TEST`, `THREATEN`, `CHARM`, `CONFESS`, `NEGOTIATE`, `STONEWALL`, `APPEAL_TO_VALUE`
- anti-patterns must include:
  - `ON_THE_NOSE` (too direct)
  - `SAME_VOICE` (everyone sounds same)
  - `INFO_DUMP` (forced exposition)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/DIALOGUE/CONVERSATION_TACTICS_CATALOG.md`

---

## 6) PROCESS (PIPELINE)
1) Read character motive/value/psy + relationship variables.
2) Define conversational goals by context (ally/enemy/intimate/authority).
3) Build tactic preferences (what tactics they default to).
4) Generate intent cards:
   - overt message + hidden goal + subtext + red lines
   - add turn events where needed (reveal, threat, commitment)
5) Build subtext patterns and avoidance list.
6) Validate against boundaries:
   - no forbidden topics/actions
   - reveal alignment where applicable
7) Emit outputs.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- intent card requires saying/doing what violates HARD moral boundaries/invariants without routing
- dialogue reveals break narrative reveal plan (if present) by revealing too early (must be flagged as S0)
- all dialogue cards lack hidden goals (flat on-the-nose dialogue system)

S1 (HIGH) if:
- tactics are identical across all contexts (no relational sensitivity)
- subtext map contradicts relationship contracts strongly

S2/S3: quality warnings.

---

## 8) NOTES FOR DOWNSTREAM ENGINES
- Speech Naturalization turns intent into human-sounding talk patterns.
- Scene Construction uses intent cards to anchor dialogue turns inside scene objectives.
- Production can later map tactics into performance notes (outside this engine).

---

LOCK: OPEN
