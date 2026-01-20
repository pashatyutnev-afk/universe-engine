# MUSIC CONTROLLERS (CTL) — REALM README (CANON)

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/00__README__MUSIC_CONTROLLERS.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 40_CTL__CONTROLLERS
FAMILY: 10_MUSIC_CONTROLLERS
DOC_TYPE: README (FAMILY)
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUSIC.REALM.README.001
OWNER: SYSTEM
ROLE: Onboarding + navigation for music-specific CTL policies (prompt contracts, viral constraints, duration policy, release variants, collisions, QA gates, etc).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Initialized canonical README for MUSIC_CONTROLLERS family with RAW-only navigation and usage rules."
- REASON: "Make CTL music policies discoverable and consistently applied in music pipelines."
- IMPACT: "Music pipeline routing can reliably reference CTL policies without guessing."
- CHANGE_ID: UE.CHG.2026-01-20.CTL.MUSIC.README.001

---

## 0) PURPOSE (LAW)
Это README семейства `10_MUSIC_CONTROLLERS`.
Он отвечает за:
- что регулируют музыкальные CTL;
- как их применять в пайплайнах;
- как навигироваться по файлам семейства (RAW-only).

---

## 1) ABSOLUTE RULES
### 1.1 RAW-only navigation
Использовать только RAW ссылки.

### 1.2 CTL role boundary
CTL задаёт политики/лимиты/обязательные гейты.
CTL не пишет “контент”, а регулирует его производство через ограничения.

### 1.3 Readiness gate is mandatory
Перед любым музыкальным выполнением ран должен пройти `READINESS_CHECK_CTL` (если рантайм включён через START).

---

## 2) WHEN TO USE THIS FAMILY
Использовать `10_MUSIC_CONTROLLERS`, когда задача относится к:
- генерации/редактуре промптов (SUNO/UDIO/универсал),
- UGC/viral требованиям,
- длительности/структуре/вариантам релиза,
- политике прав/PD/кредитов,
- порогам коллизий и памяти каталога,
- сегментам аудитории,
- качественным гейтам музыкального выхода.

---

## 3) DEFAULT APPLICATION POINTS (PIPELINE)
Рекомендуемое место применения (по порядку):
1) после выбора группы/альбома/трека — применить PROMPT_CONTRACT
2) до генерации — применить UGC/DURATION/VARIANTS политики
3) после генерации — применить COLLISION/MEMORY/QA gates
4) перед упаковкой релиза — применить CREDITS/METADATA policy

---

## 4) NAVIGATION (CANON LIST, RAW)
Family Path: `03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/`

01 — PROMPT CONTRACT  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md

02 — UGC VIRAL RULESET  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md

03 — DURATION POLICY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md

04 — RELEASE VARIANTS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/04__RELEASE_VARIANTS_CTL.md

05 — POET PD POLICY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md

06 — FINGERPRINT COLLISION THRESHOLDS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md

07 — CATALOG MEMORY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md

08 — AUDIENCE SEGMENTS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/08__AUDIENCE_SEGMENTS_CTL.md

09 — QUALITY GATES  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md

10 — SUNO PHRASEBOOK  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/10__SUNO_PHRASEBOOK_CTL.md

11 — UDIO PHRASEBOOK  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/11__UDIO_PHRASEBOOK_CTL.md

12 — NEGATIVE SPEC LIBRARY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md

13 — CREDITS METADATA POLICY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md

---

## 5) CHANGE POLICY (LOCK)
- Новая политика/контроллер добавляется только через PATCH в соответствующем файле + регистрация в `INDEX_ALL_CONTROLLERS`.
- README обновляется только PATCH и не содержит исполняемых решений.

---  
END.
