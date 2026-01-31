# NAV — REALM INDEX STANDARD (CANON)

SCOPE: Universe Engine (UE_V2)
LAYER: 04_NAV
DOC_TYPE: NAV_STANDARD
NAV_RULE: Use RAW links only
STATUS: ACTIVE
VERSION: 1.0.0
UID: UE.V2.NAV.STD.REALM_INDEX.001

PURPOSE:
Зафиксировать единый формат и правила для файлов REALM INDEX (00__REALM_INDEX__<REALM_CODE>.md),
которые являются единственной исполняемой точкой навигации внутри каждого “realm” (папки/домена).

---

## 0) ROLE IN SYSTEM (WHY IT EXISTS)
REALM INDEX — это:
- единственная “кнопка входа” в конкретную папку/домен (realm)
- место, где разрешены RAW-ссылки на под-индексы, пайпы, логи, регистры и сущности
- механизм детерминированного открытия нужных модулей без обходов и “угадывания путей”
- анти-шум фильтр: держит ссылки централизованно, чтобы сущности не разносили RAW по системе

Система навигации обязана опираться на индексы и открывать файлы через RAW, а не по PATH в голове.
(Идея “RAW-only навигации” и “не класть URL в XREF” остаётся базовой.) 

---

## 1) ABSOLUTE RULES (LAW)
R1 — ONE REALM = ONE ENTRYPOINT  
В каждом realm допускается **ровно один** основной REALM INDEX (ACTIVE).  
Если нужен “старый вход” — только DEPRECATED pointer (см. §7).

R2 — FILENAME MUST IDENTIFY REALM  
Имя файла обязано содержать идентификатор папки/домена:
`00__REALM_INDEX__<REALM_CODE>.md`
- `<REALM_CODE>` должен совпадать с кодом realm (например: BOOT, DOM_AUD, DOM_VIS)
- цель: исключить коллизии имён при наличии “тучи индексов”

R3 — PLACEMENT  
REALM INDEX лежит **в корне своего realm**:
`UE_V2/<REALM_FOLDER>/00__REALM_INDEX__<REALM_CODE>.md`

R4 — RAW LINKS LIVE HERE (NOT IN ENTITIES)  
RAW-ссылки на рабочие файлы разрешены:
- в ROOT LINK BASE
- в START/BOOT entrypoint
- в NAV_ROOT (роутинг/правила навигации)
- в REALM INDEX (и только в нём на уровне realm)
Запрещено разносить RAW по сущностям и “обычным” модулям.

R5 — XREF IS UID-ONLY  
Внутри блоков XREF / RELATED нельзя размещать URL/RAW.  
Если нужен переход — делай это через раздел LINKS (RAW) или через IDX-поинтеры.

R6 — ANTI-NOISE POLICY  
REALM INDEX не превращается в “свалку ссылок”.
Он хранит:
- минимум обязательных entrypoints
- 1–N под-индексов (если есть)
- 1–3 “target files” по типичным операциям
Остальное — через под-индексы, а не списком на 500 строк в одном файле.

R7 — DETERMINISTIC NAV  
Каждая ссылка должна быть организована так, чтобы система могла:
- выбрать нужный раздел
- открыть файл
- продолжить пайплайн
без интерпретаций и “догадываний”.

R8 — NO DUPLICATE AUTHORITY  
Если появляются дубль-индексы, дубль-правила и т.п. — один остаётся каноном (ACTIVE),
остальные переводятся в DEPRECATED pointer (см. §7).

---

## 2) REQUIRED SECTIONS (STRUCTURE)
REALM INDEX обязан содержать эти секции (в этом порядке).

### [A] HEADER / META
Стандартный заголовок (как в этом файле): SCOPE/LAYER/DOC_TYPE/NAV_RULE/STATUS/VERSION/UID.

### [B] REALM ID
- REALM_CODE
- REALM_FOLDER
- REALM_KIND (BOOT | DOMAIN | PIPE | KB | LOG | etc) — простая метка

### [C] ENTRYPOINT LINKS (RAW)
Ссылки “куда идти в первую очередь”:
- NAV_ROOT (если нужно)
- ROUTER / PIPE_DEFAULT (если домен завязан на пайпы)
- LOG entrypoints (если нужно логировать)
- REG/XREF/KB entrypoints (если этот realm зависит от них)

Правило: это короткий список “обязательных дверей”.

### [D] SUB-INDEXES (RAW)
Если realm большой — держи под-индексы:
- IDX: “сущности”
- IDX: “пайпы/протоколы”
- IDX: “критичные правила/гейты”
Каждый под-индекс — отдельный файл с тем же принципом (RAW only).

### [E] TARGET FILES (RAW)
1–3 файла, которые чаще всего открываются в задачах по этому realm.
(Пример: доменный PIPE, доменный FAIL, доменный PACK.)

### [F] OPTIONAL LINKS (RAW)
Редко нужные, но допустимые ссылки, строго сгруппированные.

### [G] XREF (UID-ONLY)
Только UID-список, без URL:
- какие стандарты/политики управляют этим realm
- какие гейты/валидации обязательны

### [H] GATES (PASS/FAIL)
Минимальная проверка целостности realm index:
PASS если:
- файл существует в корне realm
- имя соответствует R2
- ссылки RAW открываются
- нет второго ACTIVE realm index
FAIL если:
- broken RAW
- коллизия ACTIVE entrypoints
- ссылки спрятаны в XREF/RELATED

### [I] CHANGE_NOTE
Короткая история изменений (минимум).

---

## 3) TEMPLATE (COPY-PASTE)
Ниже — шаблон REALM INDEX. Его копируешь и заполняешь.

```md
# REALM INDEX — <REALM_CODE>

SCOPE: Universe Engine (UE_V2)
LAYER: 04_NAV
DOC_TYPE: REALM_INDEX
NAV_RULE: Use RAW links only
REALM_CODE: <REALM_CODE>
REALM_FOLDER: UE_V2/<REALM_FOLDER>
STATUS: ACTIVE
VERSION: 1.0.0
UID: UE.V2.NAV.REALM.<REALM_CODE>.001

PURPOSE:
Единая точка входа в realm <REALM_CODE>. Хранит только исполняемую навигацию (RAW),
не размножает ссылки по сущностям. Поддерживает детерминированное открытие файлов.

---

## [C] ENTRYPOINT LINKS (RAW)
- NAV_ROOT: <RAW>
- ROUTER (if used): <RAW>
- PIPE_DEFAULT (if used): <RAW>
- LOG_RULES (if used): <RAW>

## [D] SUB-INDEXES (RAW)
- IDX_ENTITIES: <RAW>
- IDX_PIPES: <RAW>
- IDX_GATES: <RAW>

## [E] TARGET FILES (RAW)
- TARGET_1: <RAW>
- TARGET_2: <RAW>
- TARGET_3: <RAW>

## [F] OPTIONAL LINKS (RAW)
- OPTIONAL_1: <RAW>
- OPTIONAL_2: <RAW>

## [G] XREF (UID-ONLY)
- XREF: <UID> | WHY: <reason>
- XREF: <UID> | WHY: <reason>

## [H] GATES (PASS/FAIL)
PASS IF:
- filename matches `00__REALM_INDEX__<REALM_CODE>.md`
- file is located at realm root
- all RAW links open expected content
- no second ACTIVE realm index exists
FAIL IF:
- broken RAW links
- RAW links placed inside XREF blocks
- duplicate ACTIVE entrypoints inside same realm

## [I] CHANGE_NOTE
- DATE: YYYY-MM-DD
  TYPE: MINOR|MAJOR
  SUMMARY: ...
  CHANGE_ID: ...
