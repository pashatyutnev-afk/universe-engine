# PACING & RHYTHM ENGINE (STORY-TIME)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
ENGINE: 05__PACING_RHYTHM_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.NARR.PACING.001
OWNER: SYSTEM
ROLE: Produce a story-time pacing profile and rhythm rules over beats/scenes (NOT screen-time editing rhythm).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Pacing & Rhythm Engine created for story-time: pacing profile, beat/scene density rules, and rhythm anti-pattern detection."
- REASON: "Needed a canonical pacing layer distinct from production editing/montage rhythm."
- IMPACT: "Narrative timing can be planned without touching production layer."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.NARR.PACING.001

---

## 0) PURPOSE (LAW)
Этот движок формирует **темп и ритм истории во времени сюжета (story-time)**:
- как быстро меняется состояние/информация/напряжение по ходу истории
- плотность beats и сцены (сколько значимых изменений на отрезок структуры)
- чередование типов сцен (нарастание/разрядка/переходы)
- правила ритма: где допустимы “паузы”, где нужен разгон

Важно: это НЕ монтажный ритм и НЕ длительности кадров.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- экранный ритм (screen-time) / монтаж / длительности эпизода → `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG`
- художественную атмосферу/тон как владеющий слой → `06_GENRE_STYLE_ENGINES/*`
- структуру актов/битов (это `02__STORY_STRUCTURE_ENG`)
- проектирование сцен как смысловых единиц (это `04__SCENE_CONSTRUCTION_ENG`)
- ставки/угрозы как отдельную карту (это `06__TENSION_STAKES_ENG`)

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–9)
- `CORE_IDENTITY`
- `CORE_STATE`
- `STORY_STRUCTURE_BLUEPRINT`
- `BEAT_MAP`
- `DRAMATIC_ARC_SPEC` (optional but recommended)
- `SCENE_BLUEPRINT_SET` (optional but recommended; if absent, pacing is beat-based)
- `STRUCTURE_CONSTRAINTS` (optional)
- `PLAUSIBILITY_RULESET` (optional)
- `PEAK_RELEASE_PLAN` (optional)

### PRODUCES (1–7)
- `PACING_PROFILE_STORY_TIME`
- `RHYTHM_RULESET`
- `PACING_ISSUE_REPORT`

### DEPENDS_ON
- `[02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG, 02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/PACING/`

---

## 3) DEFINITIONS (LOCAL)
- **Pacing** — скорость смысловых изменений (beaty/turns) по ходу истории.
- **Rhythm** — повторяющийся паттерн смены интенсивности (напряжение/разрядка/тишина/шок).
- **Density** — сколько значимых изменений приходится на структурный сегмент.
- **Breather** — сцена/отрезок, где давление снижается, но история всё равно движется (инфо/отношения/подготовка).

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- story-time pacing profile (по актам/сегментам/битам/сценам)
- правила плотности и чередования (rhythm rules)
- выявление провалов темпа и “пустых пробегов”
- рекомендации допустимых “breather” окон

### OUT OF SCOPE (HARD)
- screen-time timing (монтаж/кадры/длительность)
- сцены как содержательная конструкция (тут только темп, не содержание)
- стиль/атмосфера как owning-scope

### COLLISION RULE (ROUTING)
- Если спор про монтаж и длительность показа → `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG`
- Если спор про ставки/угрозы и их эскалацию → `06__TENSION_STAKES_ENG`
- Если спор про “почему это событие возможно/логично” → `01__NARRATIVE_LOGIC_ENG`
- Если спор про сцену как единицу действия → `04__SCENE_CONSTRUCTION_ENG`

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `PACING_PROFILE_STORY_TIME`
**MUST (fields):**
- `profile_id`
- `version`
- `basis` (enum: `SCENE_BASED|BEAT_BASED`)
- `segments[]` (ordered list; acts/sequences)
- `density_metrics` (summary object)
- `arc_alignment` (optional; pointers to `DRAMATIC_ARC_SPEC`)
- `breather_windows[]`
- `accelerate_windows[]`
- `open_unknowns[]`
- `scope_notes`

**Segment (minimum):**
- `segment_id` (act or sequence id)
- `range_ref` (acts/sequences)
- `intensity_level` (0..100)
- `change_density` (float; changes per segment)
- `turn_frequency` (float; turns per segment)
- `scene_mix` (object: counts by scene_role, if scene-based)
- `notes`

**Density metrics (minimum):**
- `total_beats`
- `total_scenes` (0 if beat-based)
- `avg_beats_per_act`
- `avg_turns_per_scene` (0 if beat-based)
- `peak_density_segments[]`

**VALIDATION:**
- segments cover all acts in structure blueprint
- if scene-based, every scene maps to a segment
- intensity curve must not contradict declared peak placement (if arc exists)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/PACING/PACING_PROFILE_STORY_TIME.md`

---

### B) `RHYTHM_RULESET`
**MUST (fields):**
- `ruleset_id`
- `rules[]`
- `recommended_patterns[]`
- `anti_patterns[]`
- `checks[]` (fast validation questions)

**Rule (minimum):**
- `id`
- `rule_text`
- `applies_to` (enum: `ACT|SEQUENCE|SCENE|BEAT`)
- `strength` (`HARD|SOFT`)
- `why` (short)

**Recommended pattern (minimum):**
- `pattern_id`
- `pattern_name`
- `sequence` (e.g., `ESCALATION -> BREATHER -> REVERSAL -> ESCALATION`)
- `best_for` (e.g., genre/format notes as optional)
- `risk` (what can go wrong)

**Anti-pattern (minimum):**
- `id`
- `name`
- `symptom`
- `why_bad`
- `fix_routes[]` (engine pointers or local fixes)

**VALIDATION:**
- include at least anti-patterns:
  - `FLATLINE` (no intensity change)
  - `ROLLERCOASTER_NO_PAYOFF` (peaks without resolution)
  - `DEAD_AIR` (too many low-change segments)
  - `CONSTANT_MAX` (always 90–100 intensity)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/PACING/RHYTHM_RULESET.md`

---

### C) `PACING_ISSUE_REPORT`
**MUST (fields):**
- `report_id`
- `issues[]` (can be empty)
- `severity_summary`
- `segment_hotspots[]` (where pacing problems cluster)
- `recommended_fixes[]`

**Issue (minimum):**
- `id`
- `type` (enum: `DENSITY_TOO_LOW|DENSITY_TOO_HIGH|TURN_GAPS|TOO_MANY_TRANSITIONS|PEAK_MISPLACED|BREATHER_OVERUSE|NO_RELEASE`)
- `scope_level` (enum: `ACT|SEQUENCE|SCENE`)
- `ref_ids[]` (act/scene/beat ids)
- `severity` (`S0|S1|S2|S3`)
- `why`
- `fix_route` (engine pointer or local step)

**VALIDATION:**
- S0 reserved for “story becomes non-functional” pacing faults (e.g., peak before setup with no bridge)
- every S0/S1 has `fix_route`

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/PACING/PACING_ISSUE_REPORT.md`

---

## 6) PROCESS (PIPELINE)
1) Determine basis:
   - if `SCENE_BLUEPRINT_SET` exists → `SCENE_BASED`
   - else → `BEAT_BASED`
2) Compute densities:
   - beats per act/sequence
   - turns per scene (if scenes)
3) Build intensity curve:
   - align to arc pressure points if `DRAMATIC_ARC_SPEC` exists
   - otherwise infer from beat types (reversal/reveal/confrontation = higher)
4) Identify breathers:
   - segments with necessary recovery but still forward motion
5) Detect issues:
   - dead air, constant max, peak misplacement, gaps
6) Emit outputs.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- peak density/intensity occurs before structural build-up requirements and cannot be justified by arc/logic
- pacing implies missing necessary beats (gaps that break causality or structure)
- no release window exists after peak (if peak declared)

S1 (HIGH) if:
- too many transition segments with no meaningful change
- intensity curve is flat or constantly max

S2/S3: quality warnings.

---

## 8) NOTES FOR NEIGHBOR ENGINES
- This engine informs `06__TENSION_STAKES_ENG` (how to distribute pressure).
- It must never claim ownership of editing rhythm (production).

---

LOCK: OPEN
