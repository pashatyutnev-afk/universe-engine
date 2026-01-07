# SCENE STACK 4TRACK STANDARD (SoT) (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
SPEC_TYPE: SoT
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.SPEC.SCENE_4TRACK.105
OWNER: SYSTEM
ROLE: Source-of-Truth specification for Scene Stack "4Track": defines 4 canonical tracks, event concept, ordering rules, and interfaces to Scene Pack and Track Event templates.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован Scene Stack 4Track SoT: 4 канонических трека, event модель, таймлайн/порядок, интерфейс к шаблонам"
- REASON: "Нужен единый контракт сцены и событий для KB/production без хаоса"
- IMPACT: "Narrative/Character/Visual/Sound workflows, templates 05A/05B"

---

## 0) PURPOSE (LAW)
Этот документ — SoT-спека, определяющая:
- что такое Scene Stack в системе Universe Engine,
- какие 4 трека являются каноническими,
- что такое Track Event и как он связывается с треками,
- какие минимальные поля обязаны быть у Scene Pack и Track Event,
- какие правила порядка/конфликтов обязательны.

Формат документов и поля в деталях задаются шаблонами:
- `05A__TEMPLATE__SCENE_PACK.md`
- `05B__TEMPLATE__TRACK_EVENT.md`

---

## 1) AUTHORITY & XREF (UID-first)
Primary authority:
- `01_SYSTEM_LAW/02__UID_RULES.md`
- `02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md`
- `02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md`

XREF:
- XREF: UE.LAW.UID.002 | depends_on | UID-first identity for scenes/events | 01_SYSTEM_LAW/02__UID_RULES.md
- XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | linking rules between scene/event/entities | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md
- XREF: UE.STD.SPEC.DOC_CONTROL.103 | depends_on | doc header + compliance | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- XREF: UE.STD.TPL.SCENE_PACK.105A | implements | scene pack template interface | 02_STANDARDS/01_SPECIFICATIONS/05A__TEMPLATE__SCENE_PACK.md
- XREF: UE.STD.TPL.TRACK_EVENT.105B | implements | track event template interface | 02_STANDARDS/01_SPECIFICATIONS/05B__TEMPLATE__TRACK_EVENT.md

---

## 2) DEFINITIONS
- **Scene Stack** — контейнер описания сцены как набора согласованных треков.
- **Track** — слой событий одного типа (канонически: 4).
- **Track Event** — атомарное событие на треке, с временем/порядком и связями.
- **Scene Pack** — документ-контейнер сцены (метаданные + 4 трека + ссылки на события).
- **Event Order** — порядок событий внутри сцены (временной или логический).

---

## 3) CANONICAL 4 TRACKS (ABSOLUTE)
Scene Stack всегда состоит из 4 канонических треков:

1) **NARRATIVE (Story)**
   - смысл: что происходит как история (beats, turns, stakes)
2) **CHARACTER (Agents)**
   - смысл: действия/решения персонажей, мотивации, внутренние состояния
3) **VISUAL (Cinema)**
   - смысл: визуальные события, мизансцены, кадры, постановка
4) **SOUND (Audio/Music)**
   - смысл: звук, музыка, шумы, темп, акценты

Запрещено:
- вводить “пятый канонический трек” без MAJOR изменения SoT.

Допускается:
- локальные под-треки внутри одного из 4 (как вложенная структура), но они не считаются отдельным каноническим треком.

---

## 4) SCENE PACK (MINIMUM CONTRACT)
Scene Pack — это артефакт, который обязан содержать минимум:

### 4.1 Identity
- `SCENE_UID` (UID сцены)
- `SCENE_TITLE`
- `SCENE_SCOPE` (где используется: episode/arc/chapter/etc — как строка, без жёсткого enum пока)
- `VERSION` (SemVer для scene pack как документа, если он каноничен)

### 4.2 Tracks presence (required)
- `TRACK_NARRATIVE`
- `TRACK_CHARACTER`
- `TRACK_VISUAL`
- `TRACK_SOUND`

Каждый трек может быть:
- inline (события прямо внутри Scene Pack),
- или ссылочным (список ссылок на Track Event entries).

Но наличие 4 треков обязательно.

### 4.3 Links
- XREF/REL на связанные сущности (персонажи, локации, объекты) — UID-first.

---

## 5) TRACK EVENT (MINIMUM CONTRACT)
Track Event — атомарное событие и обязано содержать минимум:

### 5.1 Identity
- `EVENT_UID`
- `EVENT_TRACK` (одно из: NARRATIVE | CHARACTER | VISUAL | SOUND)
- `EVENT_TITLE`

### 5.2 Positioning
Event обязан иметь способ упорядочивания:
- `ORDER` (целое число) — обязательное поле минимального стандарта  
Опционально:
- `TIME_CODE` (если используется таймкод)
- `BEAT` (если используется beat-структура)

### 5.3 Content
- `SUMMARY` (one-line)
- `DETAIL` (optional text)

### 5.4 Relations
- `XREF/REL` на сущности/другие события — UID-first.

---

## 6) ORDERING RULES (ABSOLUTE)
### 6.1 Primary ordering
Основной порядок внутри сцены — `ORDER` (integer ascending).

### 6.2 Cross-track synchronization
Если события на разных треках описывают один момент:
- они должны иметь одинаковый `ORDER`, или
- быть связаны через XREF `maps_to`/`references` (если order не совпадает).

Запрещено:
- иметь два события на одном треке с одинаковым `ORDER` без явного правила “same-order group”.

---

## 7) CONSISTENCY RULES (QUALITY GATES)
Scene Stack считается согласованным, если:
- у всех треков есть события или явно указано “empty track”
- нет “событий-сирот” без track принадлежности
- все XREF используют UID-first
- нет конфликтов order

---

## 8) INTERFACE TO TEMPLATES (05A / 05B)
Шаблоны обязаны реализовать контракт:
- Scene Pack template включает 4 трека и метаданные
- Track Event template включает identity + track + order + content + xref

Шаблоны могут расширять (добавлять поля), но не могут:
- менять смысл 4 треков
- убирать обязательные поля
- вводить новые канонические треки

---

## 9) MIGRATION NOTES
S0:
- привести 05A/05B шаблоны к этому контракту (identity/track/order/xref)
S1:
- определить controlled enums для `SCENE_SCOPE` (если потребуется) через отдельную спеку/модуль

---

## FINAL RULE (LOCK)
Scene Stack 4Track — SoT контракт сцены/событий.
Любое изменение количества треков или обязательных полей = MAJOR по умолчанию.
--- END.
