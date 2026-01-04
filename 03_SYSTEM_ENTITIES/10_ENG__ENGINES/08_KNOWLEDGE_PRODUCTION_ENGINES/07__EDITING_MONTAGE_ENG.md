# Editing & Montage Engine (Screen-Time)
FILE: 07__EDITING_MONTAGE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.1
ROLE: Defines screen-time rhythm (cut timing, montage patterns, transitions, continuity editing) and outputs an edit rhythm map

---

## PURPOSE

Монтаж управляет **ритмом экрана (screen-time rhythm)**:
- длиной планов
- частотой склеек
- типами переходов
- ясностью и направлением внимания
- монтажными “акцентами” и payoff-moments

Он опирается на story-time Rhythm Map (из нарратива), но не дублирует его.

---

## BOUNDARY (MANDATORY)

### THIS ENGINE OWNS (SCREEN-TIME)
- длительность кадров/планов
- правила склеек и переходов
- монтажные паттерны (montage sequences)
- continuity editing (чтобы не путать зрителя)

### THIS ENGINE DOES NOT OWN
- темп событий и “что происходит” (это Narrative Pacing & Rhythm)
- композицию/камеру/свет как исходные правила (это 08/01–04)
- музыкальную гармонию/мелодию/аранж (это 09 family)

---

## MINI-CONTRACT (MANDATORY)

- CONSUMES: shot list, STORY RHYTHM MAP (02/05), emotional arc notes, audio sync needs
- PRODUCES: EDIT RHYTHM MAP, cut rules, montage templates, sync markers list
- DEPENDS_ON: [08_KNOWLEDGE_PRODUCTION_ENGINES/03__CAMERA_CINEMATOGRAPHY_ENG.md, 02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md]
- OUTPUT_TARGET: 05_PROJECTS/*/05_PROJECT__L3/* (edit spec) + handoff to 08__SOUND_MUSIC_ENG.md and 09__MUSIC_TO_SCENE_ENG.md

---

## INPUTS

- Shot list / camera plan
- STORY RHYTHM MAP (impact/breath windows)
- Platform constraints (short/episode/film)
- Dialogue needs (if any)
- Music plan (entry/exit preferences)

---

## OUTPUTS

### 1) EDIT RHYTHM MAP (CANON)
- RHYTHM MODE (slow/medium/fast)
- AVERAGE SHOT LENGTH (range per segment)
- CUT DENSITY (cuts/min per segment)
- BREATH ZONES (longer holds)
- IMPACT ZONES (accent cuts)
- CLARITY ZONES (no fancy cuts, only clean continuity)
- TRANSITION PALETTE (allowed transitions)
- PAYOFF CUTS (planned “meaning cuts”)

### 2) CUT RULES
- continuity rule set (eyeline, direction, match)
- when to use match cuts / J-L cuts / hard cuts
- no-confusion constraints

### 3) MONTAGE TEMPLATES
- training / travel / war / investigation / reveal patterns (text templates)

### 4) SYNC MARKERS LIST
- beat points: cuts, turns, reveals, climax hits
(для звука и music-to-scene)

---

## PROCEDURE

1) Load shot list + STORY RHYTHM MAP
2) Segment the timeline (acts/blocks)
3) Assign rhythm mode per segment (breath vs impact)
4) Define average shot length ranges
5) Define transition palette (strict)
6) Create sync markers list
7) Continuity pass (clarity check)
8) Publish edit rhythm map

---

## VALIDATION RULES

- ED1: Монтаж не жертвует ясностью ради “круто”.
- ED2: Screen-time ритм согласован со story-time картой (есть breath/impact где нужно).
- ED3: Есть хотя бы один осознанный payoff cut (смысловая склейка).
- ED4: Sync markers существуют до финального звука/музыки.

---

## HANDOFF (MANDATORY)

### Receives from Narrative Pacing (02/05)
- Breath Windows → разрешены длинные удержания
- Impact Windows → акцентные склейки/ускорение
- Beat Density → целевой cut density

### Sends to Sound/Music production (08/08)
- EDIT RHYTHM MAP
- SYNC MARKERS LIST
- TRANSITION PALETTE (для whoosh/impact fx)

### Sends to Music-to-Scene (09/12)
- SYNC MARKERS LIST (turns/reveals/climax)
- Segment rhythm mode (drive/underscore/silence windows)

---

## INTEGRATION

- Upstream: Camera & Cinematography (08/03), Narrative Pacing (02/05)
- Downstream: Sound & Music production (08/08), Music To Scene (09/12)

---

OWNER: Universe Engine
LOCK: FIXED
