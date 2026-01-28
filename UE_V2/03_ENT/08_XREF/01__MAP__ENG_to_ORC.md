# XREF MAP — ENG → ORC (ALLOWLIST) (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__MAP__ENG_to_ORC.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: MAP
MAP_TYPE: ENG_TO_ORC_ALLOWLIST
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.MAP.ENG_TO_ORC.001
OWNER: SYSTEM
ROLE: Explicit allowlist: which ENG methods are permitted for each ORC pipeline. Prevents ORC from pulling arbitrary engines. Deterministic, RAW-only.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Initialized minimal working ENG→ORC allowlist for MUSIC orchestrators. No guessing beyond listed RAW links."
- REASON: "Enforce strict engine boundaries and prevent uncontrolled mixing of engines across pipelines."
- IMPACT: "ORC execution becomes auditable: only explicitly allowed engines can be used per pipeline."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.ENG2ORC.001

---

## 0) PURPOSE (LAW)
Эта карта отвечает: “какие ENG разрешены для конкретного ORC”.
Если ENG не в allowlist — его использовать нельзя.

---

## 1) ABSOLUTE RULES
### 1.1 RAW-only navigation
Только RAW ссылки.

### 1.2 Allowlist is exclusive
ORC может использовать только те ENG, которые перечислены в записи ORC.

### 1.3 Minimalism
Разрешаем минимально достаточный набор ENG.
Расширение — только PATCH этой карты.

### 1.4 Stop rule
Если для задачи нужен ENG, которого нет в allowlist → STOP: marker not confirmed (GAP in allowlist).

---

## 2) RECORD SCHEMA (CANON)
Каждая запись обязана иметь:
- ORC_UID
- ORC_RAW
- ALLOWED_ENG_RAW (0..n)
- ALLOWED_ENG_REALMS (0..n) — опционально (readme realm)
- NOTES

---

# 3) ALLOWLIST — MUSIC ORCHESTRATORS (MINIMUM WORKING SET)

## 3.1 ORC: GROUP → ALBUM
ORC_UID: UE.ORC.MUSIC.GROUP_TO_ALBUM.001
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md

ALLOWED_ENG_REALMS:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/00__README__MUSIC_FACTORY_ENGINES.md

ALLOWED_ENG_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/01__GROUP_FOUNDATION_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/03__ALBUM_BLUEPRINT_ENG.md

NOTES: Album planning uses only factory engines (group foundation + album blueprint). No sound/music engines required at this stage.

---

## 3.2 ORC: ALBUM → TRACK
ORC_UID: UE.ORC.MUSIC.ALBUM_TO_TRACK.001
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

ALLOWED_ENG_REALMS:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/00__README__MUSIC_FACTORY_ENGINES.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/00__README__TREND_GENRE_ENGINES.md

ALLOWED_ENG_RAW:
# Factory (structure + iteration + collision discipline)
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/05__DURATION_STRATEGY_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/08__NOVELTY_INJECTION_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/09__TAKE_LOG_ENG.md

# Sound/Music (content method guidance)
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/02__SONG_STRUCTURE_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/04__MELODY_HOOK_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/07__LYRICS_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/09__VOCAL_PERFORMANCE_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/11__MUSIC_STYLE_CONSISTENCY_ENG.md

# Trend (optional, only if pipeline explicitly needs it)
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md

NOTES: Trend engines are permitted but not mandatory; mandatory gates are resolved via VALIDATION_MATRIX.

---

## 3.3 ORC: TRACK TEST DOC GATE
ORC_UID: UE.ORC.MUSIC.TRACK_TEST_DOC_GATE.001
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

ALLOWED_ENG_REALMS: (none)
ALLOWED_ENG_RAW: (none)

NOTES: This ORC is matrix-driven (CTL/VAL/QA). It must not rely on ENG methods to avoid hidden logic.

---

## 3.4 ORC: RELEASE PACK
ORC_UID: UE.ORC.MUSIC.RELEASE_PACK.001
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

ALLOWED_ENG_REALMS:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/00__README__MUSIC_FACTORY_ENGINES.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/00__README__SOUND_MUSIC_ENGINES.md

ALLOWED_ENG_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/06__RELEASE_PACK_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/09_SOUND_MUSIC_ENGINES/13__MIX_MASTER_ENG.md

NOTES: Packaging uses factory release-pack method; mix/master engine is allowed only as method guidance, not as required gate.

---

## 3.5 ORC: PORTFOLIO PLANNER
ORC_UID: UE.ORC.MUSIC.PORTFOLIO_PLANNER.001
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md

ALLOWED_ENG_REALMS:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/00__README__MUSIC_FACTORY_ENGINES.md

ALLOWED_ENG_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/05__DURATION_STRATEGY_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md

NOTES: Planning may use only high-level cadence + collision discipline; no trend engines required.

---

## 3.6 ORC: POET PACK
ORC_UID: UE.ORC.MUSIC.POET_PACK.001
ORC_RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md

ALLOWED_ENG_REALMS:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/00__README__POET_PD_CORPUS_ENGINES.md

ALLOWED_ENG_RAW:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/01__PD_FILTER_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/02__POEM_FIT_SCORING_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/03__JUICE_EXTRACTOR_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/04__MOSAIC_COMPOSER_ENG.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/05__EXCERPT_COLLISION_ENG.md

NOTES: Poet pack is strictly corpus/policy-bound. No non-corpus engines allowed.

---

## 4) EXTENSION POLICY (STRICT)
Чтобы добавить ENG в allowlist ORC:
1) убедиться, что ENG файл существует (RAW)
2) добавить его в соответствующую запись ORC (PATCH)
3) при необходимости обновить PIPELINES/VALIDATION_MATRIX (PATCH)
Без PATCH — запрещено.

---

END.
