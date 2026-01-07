# SCENE STACK 4TRACK (MARKING MODULE) (CANON)
FILE: 02_STANDARDS/06_MARKING_STANDARDS/06__SCENE_STACK_4TRACK.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: MODULE
MODULE_TYPE: MARKING
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.MOD.MARKING.SCENE_4TRACK.606
OWNER: SYSTEM
ROLE: Marking module that provides practical conventions for writing Scene Stack 4Track content: track section names, event block format, ORDER usage, sync rules, and cross-track mappings. Extends Scene Stack 4Track SoT.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Модуль Scene 4Track: маркировка треков, событий, ORDER, sync и maps_to между треками"
- REASON: "Нужна единая практическая разметка сцен, чтобы они читались одинаково"
- IMPACT: "All Scene Packs and Track Events"

---

## XREF (UID-first)
XREF: UE.STD.SPEC.SCENE_4TRACK.105 | extends | marking details for scene/event writing | 02_STANDARDS/01_SPECIFICATIONS/05__SCENE_STACK_4TRACK_STANDARD.md
XREF: UE.STD.TPL.SCENE_PACK.105A | references | canonical scene pack template | 02_STANDARDS/01_SPECIFICATIONS/05A__TEMPLATE__SCENE_PACK.md
XREF: UE.STD.TPL.TRACK_EVENT.105B | references | canonical track event template | 02_STANDARDS/01_SPECIFICATIONS/05B__TEMPLATE__TRACK_EVENT.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | maps_to/references rules | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

## 0) PURPOSE
Этот модуль задаёт практику “разметки” сцен:
- как называть секции треков
- как оформлять блок события
- как использовать ORDER
- как фиксировать sync по трекам
- как связывать события между треками (maps_to/references)

---

## 1) TRACK SECTION NAMES (CANON)
Использовать ровно такие заголовки (или их эквивалент в шаблоне):
- `TRACK_NARRATIVE`
- `TRACK_CHARACTER`
- `TRACK_VISUAL`
- `TRACK_SOUND`

Запрещено:
- переименовывать треки в “Story/Agents/Cinema/Audio” без явного alias в заголовке.
Если хочется, допустимо:
- `TRACK_NARRATIVE (Story)` — но ключевое имя должно сохраняться.

---

## 2) EVENT BLOCK (PREFERRED MARKUP)
Рекомендуемый единый блок события:

- `ORDER: <int>`
- `EVENT_UID: <uid-or-placeholder>`
- `TITLE: "<...>"`
- `SUMMARY: "<one line>"`
- `DETAIL: | <optional>`
- `XREF: ...` (optional)

Минимум для канона:
- ORDER + EVENT_TRACK (если это отдельный Track Event) + SUMMARY

---

## 3) ORDER CONVENTION (PRACTICAL)
### 3.1 Recommended stepping
Рекомендуется шагать по 10:
- 10, 20, 30...
Чтобы можно было вставлять “между” (15, 25) без перестройки.

### 3.2 Same-order groups (allowed with explicit mark)
Если на треке несколько элементов на одном ORDER:
- обязателен маркер группы:

Пример:
- ORDER: 20
  GROUP: true
  ITEMS:
  - ...
  - ...

Без `GROUP: true` одинаковый ORDER на одном треке считается ошибкой.

---

## 4) SYNC BETWEEN TRACKS
### 4.1 Primary sync method
Синхронизация треков делается:
- одинаковым ORDER (предпочтительно)

### 4.2 Secondary sync method (maps_to)
Если одинаковый ORDER невозможен:
- использовать `maps_to` XREF между событиями.

Пример:
- `XREF: <EVENT_UID_TARGET> | maps_to | "same moment different representation" | <path(optional)>`

### 4.3 Notes on sync table (recommended)
Рекомендуется иметь блок:
`SYNC_ORDERS:`
- ORDER: 10 | N:yes | C:yes | V:yes | S:yes | NOTE:"..."

---

## 5) EVENT UID POLICY (PRACTICAL)
- если event живёт только внутри Scene Pack: допустим placeholder или local-style token
- если event нужен для внешних ссылок: обязан иметь настоящий UID и/или отдельный Track Event документ

Рекомендуемая практика:
- “важные” события, на которые будут ссылаться другие документы → Track Event artifact (105B template)

---

## 6) CROSS-TRACK LINKING RULES (COMMON)
Типовые связи:
- NARRATIVE → CHARACTER: `references` (мотивация/действие)
- CHARACTER → VISUAL: `maps_to` (как действие проявляется в постановке)
- VISUAL → SOUND: `references` (синхронизированные акценты)

Запрещено:
- ссылаться без UID, если событие вынесено наружу и является внутренним объектом системы.

---

## 7) EMPTY TRACK MARKING
Если трек пуст:
- `EMPTY: true`
- `EVENTS: []` или явная строка “no events”

Запрещено:
- просто “не писать трек”.

---

## 8) COMMON MISTAKES (ANTI-PATTERNS)
- разные названия треков в разных сценах
- ORDER перескакивает без причины (10 → 999)
- события без SUMMARY
- “телепорт” синхронизации без maps_to или общего ORDER

---

## 9) MIGRATION NOTES
S0:
- привести все Scene Packs к единому именованию треков и формату ORDER
S1:
- важные внешне-ссылаемые события вынести в Track Event artifacts

---

## FINAL RULE (LOCK)
Этот модуль расширяет Scene Stack 4Track SoT и задаёт практику маркировки сцены.
Изменение обязательных правил ORDER/track naming = MAJOR по умолчанию.
--- END.
