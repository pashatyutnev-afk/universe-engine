# SOUND & MUSIC (KB REALM) (CANON)
FILE: 04_KNOWLEDGE_BASE/04_SOUND_MUSIC.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: REALM
REALM: SOUND_MUSIC
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.REALM.SOUND.104
OWNER: SYSTEM
ROLE: Knowledge realm for sound and music: sound design, leitmotifs, ambience, rhythm, mix principles, sync with visuals/narrative, and audio continuity. Knowledge only, not asset storage.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MAJOR
- SUMMARY: "Нормализован realm Sound: Doc Control header + каркас разделов + правила UID-first ссылок"
- REASON: "Звук/музыка как методология должны быть структурированы"
- IMPACT: "All sound/music knowledge placement"

---

## XREF (UID-first)
XREF: UE.KB.IDX.MASTER.001 | depends_on | KB existence and navigation | 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
XREF: UE.KB.GOV.RULES.011 | governs | entity vs knowledge rules | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md
XREF: UE.STD.SPEC.SCENE_4TRACK.105 | references | scene track structure | 02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

## 0) PURPOSE
Этот realm хранит **методики и правила звука/музыки**:
- саунд-дизайн и фоли
- музыкальные темы и мотивы
- атмосферы и акустическое пространство
- ритм и темп
- микс и динамика
- синхронизация со сценой (N/V tracks)
- audio continuity

Realm не хранит wav/ stems / проекты — только знание.

---

## 1) SOUND LANGUAGE (CORE)
- “что должен чувствовать зритель” через звук
- звук как фокус внимания (mask/unmask)
- тишина как инструмент (negative audio space)

---

## 2) AMBIENCE & SPACE
- room tone / world tone
- distance cues
- reverb as geography
- layering rules (foreground vs background)

---

## 3) FOLEY & TEXTURE
- material libraries (conceptual, не файлы)
- micro-details as realism
- exaggeration caps (чтоб не мультяшно)

---

## 4) MUSIC (LEITMOTIF SYSTEM)
- motif assignment (character/faction/place/theme)
- motif evolution across arcs
- frequency cap (не “задушить” повтором)
- diegetic vs non-diegetic rules

---

## 5) RHYTHM & DYNAMICS
- rhythm sync with cuts
- tension waves (build/release)
- dynamic range policy (quiet vs loud)

---

## 6) MIX PRINCIPLES
- clarity first (dialogue intelligibility)
- frequency slotting
- sidechain rules (если надо)
- loudness target (если будет задан проектом)

---

## 7) SYNC WITH 4TRACK SCENES
Рекомендуемая практика:
- на Scene Pack указывать SOUND события с ORDER синхронизированным с N/V

Если нужно maps_to:
XREF:
- XREF: <EVENT_UID_TARGET> | maps_to | "audio sync moment" | <path(optional)>

---

## 8) AUDIO CONTINUITY
Checklist:
- ambience continuity across scene boundaries
- motif continuity (не ставить “чужую тему” без причины)
- geography consistency (пространство звучит одинаково)
- volume continuity across cuts

---

## 9) LINKING TO ENTITIES / SCENES (UID-FIRST)
Если пример про:
- персонажа/фракцию/локацию → XREF на ENTITY_UID
- сцену/ивент → XREF на SCENE_UID/EVENT_UID (если есть)

Pattern:
XREF:
- XREF: <TARGET_UID> | references | "sound/music example" | <path(optional)>

---

## 10) EXAMPLES (OPTIONAL)
> Примеры “как делаем” (ссылки UID-first на сцены/сущности).

---

## 11) OPEN QUESTIONS / TODO (OPTIONAL)
- (list)

--- END.
