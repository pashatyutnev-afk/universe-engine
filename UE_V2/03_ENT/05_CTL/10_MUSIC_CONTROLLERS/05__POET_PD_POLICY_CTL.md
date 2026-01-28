# CTL — POET PD POLICY (CANON)

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 40_CTL__CONTROLLERS
FAMILY: 10_MUSIC_CONTROLLERS
LEVEL: L2
DOC_TYPE: CTL (CONTROLLER)
ENTITY_TYPE: CONTROLLER
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUSIC.POET_PD_POLICY.001
OWNER: SYSTEM
ROLE: Enforce public-domain-only (or explicitly licensed) poetry usage. Requires KB-provenance markers, forbids guessing, defines excerpting limits, and outputs deterministic policy verdicts.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Hardened PD-only policy: explicit KB provenance requirements, no-guessing enforcement, excerpt limits, and mandatory CTL_VERDICT format."
- REASON: "Prevent copyright-risk ingestion and eliminate 'unknown origin' text usage."
- IMPACT: "Poet packs and any lyric prompts referencing poetry become auditable and rights-safe."
- CHANGE_ID: UE.CHG.2026-01-20.CTL.POETPD.001

---

## 0) PURPOSE (LAW)
Эта политика определяет, когда и как можно использовать поэзию/выдержки в системе:
- при сборке `POET_PACK_SPEC`,
- при использовании поэтических строк в `MUSIC_TRACK_PROMPT`,
- при любом “корпусном” выборе текста, который не является оригинальным текстом пользователя.

Цель: PD-only (или явно разрешённая лицензия в KB) с доказуемым происхождением (provenance).

---

## 1) ABSOLUTE RULES
### 1.1 KB source lock (no fantasy)
Любой текст, который не является оригинальным вводом пользователя, обязан иметь источник в KB.
Запрещено:
- угадывать автора/произведение,
- брать “из головы” или “из интернета без KB записи”,
- ссылаться на источник без RAW указателя на KB-объект.

### 1.2 PD-only by default
По умолчанию разрешено только PD.
Исключение возможно только если KB явно содержит лицензированное разрешение (см. 4.3), и это отмечено в provenance.

### 1.3 Provenance is mandatory
Каждый корпусный элемент (строка/выдержка/фрагмент) обязан иметь:
- KB_SOURCE_RAW (конкретный KB item/module RAW)
- SOURCE_STATUS marker (PD_CONFIRMED или LICENSE_CONFIRMED)
Если маркера нет → FAIL.

### 1.4 Excerpting, not dumping
Запрещено вставлять целые произведения “простынёй” в выдачи, если нет явного разрешающего маркера в KB.
По умолчанию: только короткие выдержки (см. 5).

### 1.5 Deterministic verdict
Контроллер обязан выдавать CTL_VERDICT в стандартном формате (см. 7).  
FAIL блокирует дальнейший пайплайн до исправления.

---

## 2) REQUIRED REFERENCES (RAW)
KB MASTER INDEX  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

KB RULES  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

KB SOURCE LOCK (NO FANTASY)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/12__KB_SOURCE_LOCK_NO_FANTASY.md

POET PACK ORC (primary consumer)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md

PD ONLY (validator)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md

VALIDATION MATRIX  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md

---

## 3) WHERE THIS CTL APPLIES
### 3.1 Artifact types (minimum)
- POET_PACK_SPEC
- MUSIC_TRACK_PROMPT (если внутри есть поэтические строки/выдержки не от пользователя)
- Любой документ, который хранит корпусные строки (по решению матрицы)

### 3.2 Invocation rule
Если артефакт содержит внешние строки поэзии:
- этот CTL обязателен до любого PD/rights валидатора.

---

## 4) DEFINITIONS (CANON)
### 4.1 “User original”
Текст, который пользователь написал сам в чате и явно передал как свой (или как разрешённый к использованию).

### 4.2 “Corpus text”
Любые строки/выдержки/фразы, которые не являются user original.

### 4.3 Allowed source statuses (must be explicit)
Разрешённые статусы источника:
- PD_CONFIRMED
- LICENSE_CONFIRMED

Запрещено:
- PD_UNKNOWN
- LICENSE_UNKNOWN
- “скорее всего PD”
- “кажется разрешено”

### 4.4 Provenance block (minimum fields)
Любой corpus text обязан ссылаться на provenance:
- KB_SOURCE_RAW: (raw link)
- SOURCE_STATUS: PD_CONFIRMED | LICENSE_CONFIRMED
- SOURCE_NOTE: коротко (что именно подтверждает статус, без угадываний)

---

## 5) EXCERPT LIMITS (DEFAULT)
Это лимиты по умолчанию, если KB не содержит специальный маркер разрешения на полный текст.

### 5.1 Per excerpt
- максимум 2–4 строки, или
- максимум 240 символов (что наступит раньше)

### 5.2 Per poet pack item
- 1–3 выдержки на item_id (каждая со своим provenance)
- запрещено собирать “полное стихотворение” кусками без явного KB-разрешения

### 5.3 Full text exception
Полный текст произведения допускается только если KB-источник содержит явный маркер:
- FULL_TEXT_ALLOWED (в любом явном виде внутри KB записи)
и одновременно SOURCE_STATUS = PD_CONFIRMED или LICENSE_CONFIRMED.

Если маркера FULL_TEXT_ALLOWED нет → полный текст запрещён.

### 5.4 Anti-collision note (recommended)
По возможности избегать самых “узнаваемых” строк, если цель — вариативность каталога.  
Если используешь известную строку — пометь это в CORPUS ITEM как “high-recognition”.

---

## 6) REQUIRED CHECKS (DETERMINISTIC)
### CHECK A — KB pointers present
- Для каждого corpus item существует KB_SOURCE_RAW.
Если отсутствует → FAIL (input absent / RAW missing).

### CHECK B — Source status marker present
- Для каждого corpus item есть SOURCE_STATUS = PD_CONFIRMED или LICENSE_CONFIRMED.
Если отсутствует → FAIL (marker not confirmed).

### CHECK C — Excerpt limits respected
- По умолчанию соблюдены лимиты 5.1–5.3.
Если нарушено → FAIL (policy violation).

### CHECK D — Provenance completeness
- У каждого corpus item есть provenance block минимум по 4.4.
Если нет → FAIL (marker not confirmed).

---

## 7) CTL VERDICT FORMAT (REQUIRED)
Каждый запуск контроллера обязан вернуть:

- CTL_ID: UE.CTL.MUSIC.POET_PD_POLICY.001
- TARGET_ARTIFACT_TYPE: (POET_PACK_SPEC | MUSIC_TRACK_PROMPT | OTHER)
- TARGET_RAW: (raw link to checked artifact)
- VERDICT: PASS | FAIL
- FINDINGS:
  - bullet list
- REQUIRED_FIXES:
  - bullet list (empty if PASS)
- FAIL_CLASS:
  - RAW missing | marker not confirmed | input absent | policy violation
- RETURN_TO:
  - raw link to repair ORC (default: POET_PACK_ORC or ALBUM_TO_TRACK_ORC)

Default return routes:
- POET_PACK fixes:
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md
- Track prompt fixes:
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

---

## 8) ENFORCEMENT NOTES (NON-OPTIONAL)
- Если provenance не доказан в KB, контроллер не “догадывается” и не ищет снаружи.
- Любая попытка обойти политику (вставить текст без KB статуса) = FAIL.
- Этот CTL не заменяет PD_ONLY_VAL, а подготавливает структуру и блокирует “неподтверждённое” ещё до валидации.

---

## 9) CHANGE POLICY (LOCK)
Любые изменения порогов/исключений:
- только PATCH
- обязательно обновить CHANGE_NOTE
- если меняется обязательность применения CTL для типов артефактов — обновить `VALIDATION_MATRIX`

---

END.
