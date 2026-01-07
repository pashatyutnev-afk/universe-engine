# VISUAL CINEMA (KB REALM) (CANON)
FILE: 04_KNOWLEDGE_BASE/03_VISUAL_CINEMA.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: REALM
REALM: VISUAL_CINEMA
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.REALM.VISUAL.103
OWNER: SYSTEM
ROLE: Knowledge realm for visual cinema: composition, camera language, lighting, color, staging, shot design, and visual continuity. Methods and rules; not asset storage.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MAJOR
- SUMMARY: "Нормализован realm Visual: Doc Control header + каркас разделов + правила UID-first ссылок на сущности/сцены"
- REASON: "Визуальная методология должна быть структурированной и канонической"
- IMPACT: "All visual knowledge placement"

---

## XREF (UID-first)
XREF: UE.KB.IDX.MASTER.001 | depends_on | KB existence and navigation | 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
XREF: UE.KB.GOV.RULES.011 | governs | entity vs knowledge rules | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md
XREF: UE.STD.SPEC.SCENE_4TRACK.105 | references | scene track structure | 02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

## 0) PURPOSE
Этот realm хранит **правила и методики визуального языка**:
- композиция и кадрирование
- камера и движение
- постановка и блокинг
- свет и цвет
- визуальные мотивы
- continuity визуального мира

Realm не хранит рендеры/ассеты/выходные файлы.
Он хранит **знание**, а не файлы производства.

---

## 1) VISUAL LANGUAGE (CORE)
- визуальная цель сцены (what audience must feel/see)
- приоритеты кадра (subject / contrast / motion)
- визуальная экономия (меньше шума — больше смысла)

---

## 2) COMPOSITION
- rule of thirds vs center framing
- leading lines
- negative space
- depth layers (FG/MG/BG)
- scale relationships

---

## 3) CAMERA (LENS + MOVEMENT)
### 3.1 Lens logic
- wide vs normal vs tele
- distortion as meaning

### 3.2 Movement logic
- static as authority
- handheld as instability
- dolly as intention
- whip as rupture

---

## 4) STAGING & BLOCKING
- who owns the frame
- power geometry (angles, height, distance)
- reveal strategies (occlusion → reveal)

---

## 5) LIGHTING
- key/fill/rim logic
- contrast as conflict
- light direction continuity
- motivated vs expressive light

---

## 6) COLOR (PALETTE SYSTEM)
- palette constraints by realm/era/faction
- warm/cool story rules
- saturation economy
- color as identity marker

---

## 7) SHOT DESIGN (SHOT TAXONOMY)
- establishing / medium / close-up / insert
- reaction shots
- gaze direction and eyelines
- match cuts / graphic matches

---

## 8) VISUAL CONTINUITY
Checklist:
- screen direction
- eyeline match
- props positions
- wardrobe continuity
- lighting continuity
- geography continuity

---

## 9) VISUAL MOTIFS (SYMBOL SYSTEM)
- motif definition
- repetition rules (frequency cap)
- motif evolution across arcs

---

## 10) LINKING TO ENTITIES / SCENES (UID-FIRST)
Если правило/пример привязан к:
- персонажу/локации/фракции → XREF на ENTITY_UID
- сцене/событию → XREF на SCENE_UID/EVENT_UID (если вынесены)

Pattern:
XREF:
- XREF: <TARGET_UID> | references | "visual example" | <path(optional)>

---

## 11) EXAMPLES (OPTIONAL)
> Примеры “как делаем” на конкретных сценах/арках.
> Только UID-first для внутренних объектов.

---

## 12) OPEN QUESTIONS / TODO (OPTIONAL)
- (list)

--- END.
