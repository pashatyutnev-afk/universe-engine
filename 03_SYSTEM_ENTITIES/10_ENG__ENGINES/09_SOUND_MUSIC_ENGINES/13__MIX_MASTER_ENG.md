# Mix / Master Engine
FILE: 13__MIX_MASTER_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines reproducible mix and master logic (balance targets, headroom, dynamics intent, loudness targets, translation checks, clarity priorities, spatial staging, and artifact control) without tool-specific prescriptions; produces Mix/Master Specs, Priority Stacks, Loudness/Dynamics Targets, Translation Checklists, Delivery Formats, and QC Gates aligned with arrangement, vocals, sound design, and platform requirements

---

## PURPOSE

Микс/мастер — это “довести до готового релиза”:
- баланс громкостей и ролей
- читаемость лидов/вокала
- контроль динамики (но без убийства)
- пространство (ширина/глубина)
- чистота (артефакты, резонансы, грязь)
- переводимость на разных устройствах
- соответствие платформе (стрим/кино/игра)

Движок фиксирует **цели и проверки**, чтобы результат был воспроизводим.

---

## NON-GOALS

- не навязывает конкретные плагины/цепочки
- не заменяет аранжировку (если аранж сломан — миксом не спасти)
- не пишет музыку
Он задаёт **стандарты выхода**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Arrangement Spec (09.08) + Register Plan (RP)
- Vocal Spec (09.09) + safe zones
- Sound Design Spec (09.10) + palette/budget
- Style Consistency (09.11) + mix aesthetic targets
- Music-to-Scene (09.12) + dialogue rules (if any)
- Format constraints (07 Production formats)

### PRODUCES
- MIX/MASTER SPEC (MMS) — canonical artifact
- PRIORITY STACK (PS)
- LOUDNESS + DYNAMICS TARGETS (LDT)
- SPACE/STAGE PLAN (SSP)
- ARTIFACT CONTROL LIST (ACL)
- TRANSLATION CHECKLIST (TCL)
- DELIVERY FORMAT SHEET (DFS)
- MIX/MASTER QC GATES (MMG)

### DEPENDS_ON
- Upstream engines for clarity constraints:
  - 09.08/09.09/09.10/09.11
- Editing/sound production layer if picture/scene

### OUTPUT_TARGET
- Feeds:
  - final delivery artifacts
  - QA validation
  - governance versioning

---

## CANON TERMS

### PRIORITY STACK
Что должно быть слышно “всегда” и что может уступать.

### HEADROOM
Запас по уровню/плотности для контролируемой динамики.

### TRANSLATION
Как микс переносится:
телефон/наушники/машина/мониторы/TV.

### LOUDNESS TARGET
Целевой уровень громкости (по платформе/формату).

### ARTIFACTS
Щелчки, клипы, резонансы, грязь, шипение, pumping, harshness.

---

## CORE RULES (CANON)

### MM1 — Lead clarity is the top constraint
Лид/вокал (если есть) должен быть читаем всегда согласно PS.

### MM2 — Arrangement-first principle
Если миксу мешают конфликты аранжа → эскалировать в 09.08/09.10, а не “лечить” бесконечно.

### MM3 — Loudness follows purpose
LDT выбирается по формату:
- film/series: preserve dynamics
- streaming: competitive but not crushed
- game: flexible + stems

### MM4 — Translation is mandatory
TCL обязателен: микс должен работать на минимум 4 средах.

### MM5 — Style aesthetic is enforced
SSP + tonal balance должны совпадать со style bible (09.11).

### MM6 — Artifact control is explicit
ACL фиксирует типичные проблемы и проверки.

### MM7 — Reproducibility
MMS достаточно точен, чтобы другой инженер мог повторить intent.

---

## REQUIRED ARTIFACT A: MIX/MASTER SPEC (MMS)

### MMS SCHEMA (CANON)

Header:
- MMS_ID:
- TRACK_ID / CUE_ID:
- STYLE_ID (MSB_ID):
- FORMAT TARGET:
  - streaming / film / game / youtube
- VERSION:
- STATUS:
  - draft | canon | deprecated

Priority:
- PRIORITY STACK (PS ref)

Balance intent:
- LOW-END INTENT:
  - tight / heavy / cinematic / minimal
- MID CLARITY INTENT:
  - vocal-forward / instrument-forward
- TOP-END INTENT:
  - smooth / bright / airy / dark

Dynamics:
- LOUDNESS + DYNAMICS TARGETS (LDT ref)
- TRANSIENT POLICY:
  - soft/med/hard
- PUMPING POLICY:
  - none/allowed in drops only/etc.

Space:
- SPACE/STAGE PLAN (SSP ref)
- MONO COMPATIBILITY POLICY:
  - strict / relaxed (but defined)

Artifacts:
- ARTIFACT CONTROL LIST (ACL ref)

Translation:
- TRANSLATION CHECKLIST (TCL ref)

Delivery:
- DELIVERY FORMAT SHEET (DFS ref)

Rule:
- MMS is a full “delivery intent” spec.

---

## REQUIRED ARTIFACT B: PRIORITY STACK (PS)

### PS SCHEMA (CANON)

- PS_ID:
- MMS_ID:

Always-on priorities (ordered):
1) LEAD / VOCAL (if present)
2) RHYTHM CORE (kick/snare/primary pulse)
3) BASS FOUNDATION
4) HOOK SUPPORT (signature layer)
5) HARMONY BED
6) FX / EAR-CANDY
7) TEXTURES / AMBIENCE

Rules:
- In dialogue scenes: dialogue > music (if applicable, via 09.12 DSP)
- “Never bury the hook” rule if hook-driven style

---

## REQUIRED ARTIFACT C: LOUDNESS + DYNAMICS TARGETS (LDT)

### LDT SCHEMA (CANON)

- LDT_ID:
- FORMAT TARGET:
- TARGET LOUDNESS:
  - (value left as variable per platform policy)
- TRUE PEAK POLICY:
  - keep margin (policy)
- DYNAMIC RANGE INTENT:
  - wide / medium / tight
- LIMITING INTENT:
  - gentle / moderate / aggressive
- BUS COMP INTENT:
  - none/light/med

Rule:
- Store targets as policy-level values; platform presets can live elsewhere.

---

## REQUIRED ARTIFACT D: SPACE/STAGE PLAN (SSP)

### SSP SCHEMA (CANON)

- SSP_ID:
- MMS_ID:

Stage:
- WIDTH INTENT:
  - narrow / medium / wide / cinematic
- DEPTH INTENT:
  - flat / layered / deep
- CENTER POLICY:
  - what stays centered (vocal, kick, bass)
- AMBIENCE POLICY:
  - dry / med / wet
- REVERB CHARACTER:
  - short room / plate / hall / dark / bright (descriptive)
- DELAY POLICY:
  - none / slap / tempo delays (where)

Compatibility:
- MONO CHECK RULE:
  - must pass / warn / ignore (but decide)

Rule:
- SSP keeps spatial identity consistent.

---

## REQUIRED ARTIFACT E: ARTIFACT CONTROL LIST (ACL)

### ACL SCHEMA (CANON)

- ACL_ID:
- MMS_ID:

Common artifacts + checks:
- CLIPPING CHECK:
  - none allowed
- TRUE PEAK CHECK:
  - margin policy
- HARSHNESS CHECK:
  - top-end fatigue rule
- MUD CHECK:
  - low-mid congestion rule
- PUMPING CHECK:
  - allowed only where intentional
- RESONANCE CHECK:
  - scan for ringing notes (policy)
- SIBILANCE CHECK (if vocal):
  - must be controlled but not lisp
- NOISE CHECK:
  - tails, hiss, hum
- PHASE CHECK:
  - stereo elements not collapsing

Rule:
- ACL is the “no surprises” list.

---

## REQUIRED ARTIFACT F: TRANSLATION CHECKLIST (TCL)

### TCL SCHEMA (CANON)

- TCL_ID:
- MMS_ID:

Test environments (minimum 4):
1) Studio monitors (reference)
2) Headphones
3) Phone speaker
4) Car/TV/small Bluetooth

What to check:
- vocal/lead readability
- kick/bass audibility without boom
- harshness fatigue
- mono collapse issues
- reverb/delay not washing out
- overall energy vs intent

Pass rule:
- 0 critical fails
- <=2 warnings with documented compromises

---

## REQUIRED ARTIFACT G: DELIVERY FORMAT SHEET (DFS)

### DFS SCHEMA (CANON)

- DFS_ID:
- MMS_ID:

Deliverables:
- MAIN MASTER:
  - format (wav), sample rate, bit depth (policy-level)
- STEMS (if required):
  - drums / bass / music / vocals / fx
- ALT VERSIONS (optional):
  - instrumental / a cappella / clean / loopable / 15s/30s cutdowns
- LOOP POINTS (if game):
  - start/end markers

Rule:
- DFS makes output operational and repeatable.

---

## REQUIRED ARTIFACT H: MIX/MASTER QC GATES (MMG)

### MMG SCHEMA (CANON)

Gates:
1) Priority clarity gate:
   - PS “always-on” elements readable
2) Arrangement compatibility gate:
   - no unresolvable masking conflicts (else escalate upstream)
3) Loudness/dynamics gate:
   - meets LDT intent and format target
4) Space identity gate:
   - SSP matches style bible and doesn’t break mono policy
5) Artifact gate:
   - ACL checks pass (no critical artifacts)
6) Translation gate:
   - TCL passes across environments
7) Delivery gate:
   - DFS deliverables prepared and consistent
8) Reproducibility gate:
   - MMS+PS+LDT+SSP+ACL+TCL+DFS allow recreation

Rule:
- Fail 2+ gates → revise; critical fail → block release.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- lead disappears on phone
- bass booms in car but vanishes on phone
- chorus collapses in mono
- harshness causes fatigue within 30s
- mix is too dense; no headroom for master
- limiter pumping in verses (unintended)

Fix options:
- adjust PS: give lead protected space
- revisit arrangement register conflicts (09.08 RP)
- simplify sound design in mid band (09.10)
- refine space plan: keep center stable, reduce wash
- adjust dynamics intent to format (LDT)
- enforce ACL and rerun translation tests

---

## PROCEDURE (HOW TO RUN)

1) Read upstream specs: arrangement/vocal/sound design/style
2) Define PS (what must always be heard)
3) Define LDT (format loudness/dynamics intent)
4) Define SSP (space identity + mono policy)
5) Define ACL checks and run early
6) Mix to PS priorities and SSP intent
7) Master to LDT intent without breaking PS
8) Run TCL translation tests
9) Compile DFS deliverables
10) Run MMG gates and lock version

---

## QC CHECKLIST (MANDATORY)

- priorities clear and protected?
- loudness/dynamics matches purpose?
- space identity consistent with style?
- artifacts checked and controlled?
- translation tests passed?
- deliverables complete?
- reproducible spec exists?

---

## VALIDATION RULES

- MMV1: Priority elements are consistently readable across the track.
- MMV2: Loudness and dynamics match format intent without audible damage.
- MMV3: Spatial identity matches style and remains compatible per mono policy.
- MMV4: No critical artifacts; controlled harshness/mud/pumping.
- MMV5: Translation passes across required environments.
- MMV6: Deliverables meet DFS and are consistent.
- MMV7: Spec is reproducible and operational.

---

OWNER: Universe Engine
LOCK: FIXED
