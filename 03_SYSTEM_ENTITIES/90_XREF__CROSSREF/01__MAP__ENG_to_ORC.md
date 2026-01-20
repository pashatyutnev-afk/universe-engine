# XREF MAP — ENG → ORC (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__MAP__ENG_to_ORC.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: MAP
MAP_TYPE: ENG_TO_ORC
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.MAP.ENG_TO_ORC.001
OWNER: SYSTEM
ROLE: Deterministic allowlist: which ENG realms/engines are permitted inside each ORC pipeline step (no guessing).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Initialized minimal ENG→ORC allowlist for music orchestrators. Added strict policy for extending map."
- REASON: "Remove implicit assumptions and prevent ORC from pulling arbitrary engines."
- IMPACT: "Routing becomes auditable: ORC may use only the engines explicitly allowed here."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.ENG2ORC.001

---

## 0) PURPOSE (LAW)
Эта карта фиксирует разрешённые связки:
- ORC (пайплайн/шаг) → допустимые ENG (реалмы/движки)

Если связка не прописана здесь, она считается запрещённой (GAP).

---

## 1) ABSOLUTE RULES
### 1.1 RAW-only navigation
Использовать только RAW ссылки из ROOT LINK BASE или присланные пользователем.

### 1.2 Allowlist only
Разрешено только то, что явно перечислено в REGISTRY.
Всё остальное = GAP.

### 1.3 No guessing
Нельзя подставлять “логично подходит” без регистрации в этой карте.

---

## 2) RECORD SCHEMA (CANON)
Каждая запись обязана содержать:
- ORC_ID
- ORC_RAW
- ALLOWED_ENG_REALMS (список реалмов ENG, RAW на README реалма)
- OPTIONAL_ALLOWED_ENG (если нужно сузить до конкретных файлов)
- NOTES (границы применения)

---

## 3) CANON REALM REFS (ENG)
Эти ссылки используются в allowlist как “реалмы”.

### 3.1 MUSIC FACTORY ENGINES (ENG REALM)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/00__README__MUSIC_FACTORY_ENGINES.md

### 3.2 SOUND MUSIC ENGINES (ENG REALM)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md

### 3.3 TREND GENRE ENGINES (ENG REALM)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/00__README__TREND_GENRE_ENGINES.md

### 3.4 POET PD CORPUS ENGINES (ENG REALM)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/00__README__POET_PD_CORPUS_ENGINES.md

### 3.5 NAMING IDENTITY ENGINES (ENG REALM)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/00__README__NAMING_IDENTITY_ENGINES.md

---

## 4) REGISTRY (MINIMUM CANON SET — MUSIC ORC)

### 4.1 ORC: GROUP → ALBUM
ORC_ID: ORC.MUSIC.GROUP_TO_ALBUM.001  
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md

ALLOWED_ENG_REALMS (RAW):
- MUSIC_FACTORY_ENGINES
- NAMING_IDENTITY_ENGINES

NOTES:
- Разрешены ENG, которые помогают собрать основу группы и построить альбомный blueprint.
- Всё, что касается аудио-микса, здесь не является обязательным.

---

### 4.2 ORC: ALBUM → TRACK
ORC_ID: ORC.MUSIC.ALBUM_TO_TRACK.001  
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

ALLOWED_ENG_REALMS (RAW):
- MUSIC_FACTORY_ENGINES
- SOUND_MUSIC_ENGINES
- TREND_GENRE_ENGINES
- NAMING_IDENTITY_ENGINES

NOTES:
- Разрешены ENG для проектирования трека, структуры, хука, а также правил naming/identity.

---

### 4.3 ORC: TRACK TEST DOC GATE
ORC_ID: ORC.MUSIC.TRACK_TEST_DOC_GATE.001  
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

ALLOWED_ENG_REALMS (RAW):
- MUSIC_FACTORY_ENGINES
- SOUND_MUSIC_ENGINES

NOTES:
- Этот ORC управляет документ-гейтами и тестовыми документами трека.
- Любые “внешние” ENG запрещены без регистрации.

---

### 4.4 ORC: RELEASE PACK
ORC_ID: ORC.MUSIC.RELEASE_PACK.001  
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

ALLOWED_ENG_REALMS (RAW):
- MUSIC_FACTORY_ENGINES
- NAMING_IDENTITY_ENGINES

NOTES:
- Здесь основная задача: упаковка и навигационная целостность, naming, комплектность.

---

### 4.5 ORC: PORTFOLIO PLANNER
ORC_ID: ORC.MUSIC.PORTFOLIO_PLANNER.001  
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md

ALLOWED_ENG_REALMS (RAW):
- TREND_GENRE_ENGINES
- MUSIC_FACTORY_ENGINES
- NAMING_IDENTITY_ENGINES

NOTES:
- Планирование портфеля допускает трендовые и идентификационные ENG.
- При появлении нового “planner” ENG — сначала регистрируем здесь.

---

### 4.6 ORC: POET PACK
ORC_ID: ORC.MUSIC.POET_PACK.001  
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md

ALLOWED_ENG_REALMS (RAW):
- POET_PD_CORPUS_ENGINES
- MUSIC_FACTORY_ENGINES
- NAMING_IDENTITY_ENGINES

NOTES:
- Этот ORC использует корпус/фильтры/сборку поэтов и связывает это с выпуском.

---

## 5) EXTENSION POLICY (STRICT)
Чтобы добавить новую связку ORC → ENG:
1) иметь RAW на ORC файл и на ENG реалм (README)
2) добавить запись в REGISTRY (PATCH)
3) если требуется конкретизация — добавить OPTIONAL_ALLOWED_ENG (конкретные файлы ENG)
4) зафиксировать CHANGE_NOTE

---

END.
