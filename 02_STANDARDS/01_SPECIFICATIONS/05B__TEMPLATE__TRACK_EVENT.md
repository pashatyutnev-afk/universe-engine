# TEMPLATE — TRACK EVENT (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/05B__TEMPLATE__TRACK_EVENT.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: TEMPLATE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.TPL.TRACK_EVENT.105B
OWNER: SYSTEM
ROLE: Canonical template for a Track Event artifact that conforms to Scene Stack 4Track SoT. Used when events are stored as separate artifacts.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Шаблон Track Event приведён к контракту 4Track: EVENT_UID + EVENT_TRACK + ORDER + SUMMARY + XREF UID-first"
- REASON: "Нужен атомарный event формат для разнесённых событий"
- IMPACT: "Scene authoring, linking, KB entity passports"

---

## XREF (UID-first)
XREF: UE.STD.SPEC.SCENE_4TRACK.105 | implements | this template follows 4Track contract | 02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking policy | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md
XREF: UE.STD.SPEC.DOC_CONTROL.103 | depends_on | header/compliance format | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

---

# TRACK EVENT — COPY TEMPLATE (INSTANCE)
> Инструкция: скопируй этот блок для нового события и заполни поля.
> Если это канонический event-документ — `LOCK: FIXED` и регистрируется по правилам.
> Если черновик — `LOCK: OPEN`, не канон.

---

## DOC CONTROL (INSTANCE HEADER)
FILE: <path-to-your-track-event.md>
SCOPE: Universe Engine
LAYER: <your-layer-or-KB-realm>
DOC_TYPE: ARTIFACT
ARTIFACT_TYPE: TRACK_EVENT
LEVEL: L2
STATUS: <DRAFT|ACTIVE>
LOCK: <OPEN|FIXED>
VERSION: 0.1.0
UID: <TRACK_EVENT_DOC_UID>        # UID документа (если канон)
OWNER: <owner/team>
ROLE: Track Event instance (atomic event)

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "..."
- REASON: "..."
- IMPACT: "..."

---

## 1) EVENT IDENTITY (REQUIRED)
EVENT_UID: <EVENT_UID>            # UID сущности события (system identity for event)
EVENT_TITLE: "<short title>"

EVENT_TRACK: <NARRATIVE|CHARACTER|VISUAL|SOUND>   # REQUIRED enum by 4Track SoT
ORDER: <integer>                                  # REQUIRED ordering key

---

## 2) EVENT CONTENT (REQUIRED MINIMUM)
SUMMARY: "<one-line summary>"

DETAIL: |
  <optional expanded description>
  <can be multi-paragraph>

---

## 3) EVENT CONTEXT (OPTIONAL)
SCENE_UID: <SCENE_UID or null>     # link back to scene entity
SCENE_PACK_REF: <path/uid optional>

TIME_CODE: "<optional>"
BEAT: "<optional>"

---

## 4) PARTICIPANTS / OBJECTS (UID-first, OPTIONAL)
CHARACTERS:
- CHARACTER_UID: <UID> | ROLE: "<role>" | NOTE: "<short>"

OBJECTS:
- OBJECT_UID: <UID> | NOTE: "<short>"

LOCATION_UID: <UID or null>

---

## 5) RELATIONS / XREF (UID-first)
XREF:
- XREF: <UID_TARGET> | references | "<why>" | <path(optional)>
- XREF: <UID_TARGET> | depends_on | "<why>" | <path(optional)>
- XREF: <UID_TARGET> | maps_to | "<mapping reason>" | <path(optional)>

---

## 6) CONSISTENCY NOTES (OPTIONAL)
CHECKS:
- ORDER_UNIQUE_ON_TRACK: <true|false|n/a>
- SYNC_WITH_OTHER_TRACKS: "<how (same ORDER / maps_to / none)>"

NOTES:
- "<free notes>"

--- END OF TEMPLATE
