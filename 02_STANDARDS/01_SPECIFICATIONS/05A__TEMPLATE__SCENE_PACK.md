# TEMPLATE — SCENE PACK (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/05A__TEMPLATE__SCENE_PACK.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: TEMPLATE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.TPL.SCENE_PACK.105A
OWNER: SYSTEM
ROLE: Canonical template for creating a Scene Pack artifact that conforms to Scene Stack 4Track SoT. Provides a ready-to-copy scene document structure.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Шаблон Scene Pack приведён к контракту 4Track: SCENE_UID + 4 трека + ORDER + XREF UID-first"
- REASON: "Нужна единая копируемая форма"
- IMPACT: "Scene authoring, KB realms, production pipeline"

---

## XREF (UID-first)
XREF: UE.STD.SPEC.SCENE_4TRACK.105 | implements | this template follows 4Track contract | 02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md
XREF: UE.STD.SPEC.DOC_CONTROL.103 | depends_on | header/compliance format | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking policy | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md
XREF: UE.STD.TPL.TRACK_EVENT.105B | references | use for atomic events if separated | 02_STANDARDS/01_SPECIFICATIONS/05B__TEMPLATE__TRACK_EVENT.md

---

# SCENE PACK — COPY TEMPLATE (INSTANCE)
> Инструкция: скопируй этот блок для новой сцены и заполни поля.
> Если это канонический Scene Pack документ, он тоже должен иметь свой Doc Control header (верхний).  
> Если это рабочий черновик — можешь поставить `LOCK: OPEN` и не регистрировать в индексе.

---

## DOC CONTROL (INSTANCE HEADER)
FILE: <path-to-your-scene-pack.md>
SCOPE: Universe Engine
LAYER: <your-layer-or-KB-realm>
DOC_TYPE: ARTIFACT
ARTIFACT_TYPE: SCENE_PACK
LEVEL: L2
STATUS: <DRAFT|ACTIVE>
LOCK: <OPEN|FIXED>
VERSION: 0.1.0
UID: <SCENE_PACK_DOC_UID>   # UID документа (если он канон). Не путать с SCENE_UID ниже.
OWNER: <owner/team>
ROLE: Scene Pack instance (scene container)

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "..."
- REASON: "..."
- IMPACT: "..."

---

## 1) SCENE IDENTITY (REQUIRED)
SCENE_UID: <SCENE_UID>            # UID сущности сцены (story-world entity). UID-first.
SCENE_TITLE: "<scene title>"
SCENE_SCOPE: "<episode|chapter|arc|sequence|...>"
SCENE_ORDER_GLOBAL: <int-or-null> # опционально: порядок сцены в эпизоде/главе

SCENE_LOG_LINE: "<one-line logline>"
SCENE_STATUS: "<draft|final|locked|...>" # свободная строка (не системный STATUS)

---

## 2) SCENE CONTEXT (OPTIONAL BUT RECOMMENDED)
SETTING:
- LOCATION_UID: <UID or null>
- TIME: "<time-of-day/period>"
- WEATHER: "<optional>"
- ATMOSPHERE: "<one-line>"

CAST (UID-first):
- CHARACTER_UID: <UID> | ROLE: <main/support/extra> | NOTE: "<short>"
- CHARACTER_UID: <UID> | ROLE: <...> | NOTE: "<short>"

OBJECTS (UID-first, optional):
- OBJECT_UID: <UID> | NOTE: "<short>"
- OBJECT_UID: <UID> | NOTE: "<short>"

GOALS / STAKES:
- GOAL: "<what must be achieved>"
- STAKES: "<what happens if fail>"

---

## 3) RELATIONS / XREF (UID-first)
> Здесь — связи сцены с сущностями/доками/арками. Формат единый.

XREF:
- XREF: <UID_TARGET> | references | "<why>" | <path(optional)>
- XREF: <UID_TARGET> | depends_on | "<why>" | <path(optional)>

---

## 4) TRACKS (CANONICAL 4TRACK)
Правило: всегда 4 трека. Если трек пуст — явно укажи `EMPTY: true`.

### 4.1 TRACK_NARRATIVE (REQUIRED)
EMPTY: false
EVENTS:
- ORDER: 10
  EVENT_UID: <UID or local placeholder>
  TITLE: "<beat/event title>"
  SUMMARY: "<one-line>"
  DETAIL: |
    <optional paragraph>
  XREF:
    - XREF: <UID_TARGET> | references | "<why>" | <path(optional)>

- ORDER: 20
  EVENT_UID: <...>
  TITLE: "<...>"
  SUMMARY: "<...>"
  DETAIL: |
    <...>
  XREF:
    - XREF: <UID_TARGET> | references | "<why>" | <path(optional)>

---

### 4.2 TRACK_CHARACTER (REQUIRED)
EMPTY: false
EVENTS:
- ORDER: 10
  EVENT_UID: <...>
  TITLE: "<decision/action>"
  SUMMARY: "<one-line>"
  DETAIL: |
    <...>
  XREF:
    - XREF: <CHARACTER_UID> | references | "actor involved" | <path(optional)>

- ORDER: 20
  EVENT_UID: <...>
  TITLE: "<...>"
  SUMMARY: "<...>"
  DETAIL: |
    <...>

---

### 4.3 TRACK_VISUAL (REQUIRED)
EMPTY: false
EVENTS:
- ORDER: 10
  EVENT_UID: <...>
  TITLE: "<visual beat>"
  SUMMARY: "<one-line>"
  DETAIL: |
    <camera/mise-en-scene notes>
  XREF:
    - XREF: <UID_TARGET> | references | "<why>" | <path(optional)>

- ORDER: 20
  EVENT_UID: <...>
  TITLE: "<...>"
  SUMMARY: "<...>"
  DETAIL: |
    <...>

---

### 4.4 TRACK_SOUND (REQUIRED)
EMPTY: false
EVENTS:
- ORDER: 10
  EVENT_UID: <...>
  TITLE: "<sound/music beat>"
  SUMMARY: "<one-line>"
  DETAIL: |
    <SFX/MX notes>
  XREF:
    - XREF: <UID_TARGET> | references | "<why>" | <path(optional)>

- ORDER: 20
  EVENT_UID: <...>
  TITLE: "<...>"
  SUMMARY: "<...>"
  DETAIL: |
    <...>

---

## 5) SYNC CHECK (OPTIONAL QUALITY BLOCK)
> Быстрый чек согласованности: какие ORDER синхронизированы по трекам.

SYNC_ORDERS:
- ORDER: 10 | NARRATIVE: yes | CHARACTER: yes | VISUAL: yes | SOUND: yes | NOTE: "<optional>"
- ORDER: 20 | NARRATIVE: yes | CHARACTER: yes | VISUAL: yes | SOUND: yes | NOTE: "<optional>"

---

## 6) NOTES (FREE)
NOTES:
- "<any extra>"

--- END OF TEMPLATE
