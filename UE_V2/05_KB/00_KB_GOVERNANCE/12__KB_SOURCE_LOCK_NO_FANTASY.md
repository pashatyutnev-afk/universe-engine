# KB LAW — SOURCE LOCK / NO FANTASY (CANON)

FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/12__KB_SOURCE_LOCK_NO_FANTASY.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 04_KNOWLEDGE_BASE
REALM: 00_KB_GOVERNANCE
DOC_TYPE: LAW (KB_GOVERNANCE)
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.LAW.SOURCE_LOCK.001
OWNER: SYSTEM
ROLE: Absolute KB boundary law. Forbids “fantasy sources”: no external facts/text/assets may enter runtime unless represented as KB-tracked source with RAW provenance markers. Defines mandatory provenance markers used by CTL/VAL.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Hardened KB Source Lock: mandatory provenance markers (PD_CONFIRMED / LICENSE_CONFIRMED / FULL_TEXT_ALLOWED), RAW-only references, and strict boundary enforcement for any non-user-origin content."
- REASON: "Prevent uncontrolled ingestion, copyright risk, and unverifiable ‘from the internet’ claims."
- IMPACT: "All corpus/text/facts used by pipelines become auditable and validator-compatible."
- CHANGE_ID: UE.CHG.2026-01-20.KB.SOURCELOCK.001

---

## 0) PURPOSE (LAW)
Это закон “Источник только через KB”.
Система не имеет права использовать:
- факты, тексты, данные, изображения, выдержки, цитаты, биографии, справочные сведения,
- любые материалы, которые не являются “user original”,
если они не представлены как KB-объект с явными маркерами происхождения (provenance) и статусами разрешённости.

---

## 1) DEFINITIONS (CANON)
### 1.1 User original
Контент, который пользователь явно передал как свой ввод в чате (или явно разрешённый им текст/данные).

### 1.2 External / non-user content
Любой контент, который не является user original:
- corpus/поэзия/цитаты
- факты/справка
- данные/таблицы/перечни
- любые “нашёл в сети” материалы

### 1.3 KB-tracked source
Источник считается допустимым только если он:
- представлен в Knowledge Base как объект/запись (module/item/record),
- имеет RAW pointer на KB объект,
- содержит обязательные маркеры provenance и статуса (см. 3).

---

## 2) ABSOLUTE BOUNDARY RULES
### 2.1 RAW-only
Любые ссылки на KB-источники — только RAW.

### 2.2 No fantasy sources (absolute)
Запрещено использовать внешние материалы “на словах”:
- “в Википедии написано”
- “в интернете есть”
- “по памяти”
- “примерно так”
Пока нет KB-tracked source → считается отсутствующим.

### 2.3 No external lookup in runtime by default
Если задаче нужен внешний источник:
- сначала должен появиться KB-объект/запись источника (с provenance),
- только потом материалы из него могут использоваться в пайплайнах.

### 2.4 Stop conditions
Если требуется внешний контент и нет KB-tracked source:
- STOP: input absent (KB source missing)
или
- STOP: marker not confirmed (provenance/status missing)

---

## 3) MANDATORY PROVENANCE MARKERS (REQUIRED)
Любой KB-tracked source, из которого берётся non-user content, обязан содержать минимум:

### 3.1 KB_SOURCE_RAW
RAW ссылка на конкретный KB объект, который представляет источник.

### 3.2 SOURCE_STATUS (required, strict enum)
Допустимые статусы:
- PD_CONFIRMED
- LICENSE_CONFIRMED

Запрещены любые прочие/свободные формулировки:
- PD_UNKNOWN
- LICENSE_UNKNOWN
- “скорее всего PD”
- “кажется разрешено”

### 3.3 SOURCE_NOTE (required)
Короткая заметка, что именно подтверждает статус.
Без догадок и без “кажется”.

### 3.4 FULL_TEXT_ALLOWED (optional, explicit)
Если в пайплайне используется полный текст произведения (а не короткая выдержка),
в KB-источнике должен быть явный маркер:
- FULL_TEXT_ALLOWED

Если маркера нет — полный текст запрещён (использовать только выдержки).

---

## 4) KB SCOPE (BOUNDARIES)
### 4.1 KB Inputs
- KB modules/items/records, созданные и сохранённые в репозитории как документы.
- User original (как отдельный режим: “не требует KB источника”).

### 4.2 KB Outputs
- Разрешённые к использованию “источники” и “корпуса” для доменных пайплайнов.
- Provenance-ready записи, которые могут пройти CTL/VAL.

### 4.3 KB Boundaries
- KB не принимает “внешнюю правду” без фиксации.
- Всё external должно быть: (a) зафиксировано в KB, (b) иметь SOURCE_STATUS, (c) иметь provenance markers.

### 4.4 KB Entry RAW
KB MASTER INDEX (entrypoint)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

KB RULES
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

---

## 5) INTERFACES (RAW)
### 5.1 Policy interface (MUSIC poetry)
POET PD POLICY (CTL)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md

PD ONLY (VAL)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md

POET PACK ORC (consumer)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md

---

## 6) ENFORCEMENT RULES (HOW TO USE THIS LAW)
### 6.1 If a pipeline needs external content
Pipeline обязан:
1) запросить KB scope link (или KB source record RAW),
2) убедиться, что у источника есть SOURCE_STATUS,
3) применить доменный CTL/VAL (если матрица требует),
4) только затем использовать контент.

### 6.2 If provenance is incomplete
Если нет KB_SOURCE_RAW или SOURCE_STATUS:
- это не “почти готово”
- это FAIL и STOP (marker not confirmed)

### 6.3 Allowed minimal excerpt mode (default)
Если FULL_TEXT_ALLOWED нет:
- использовать только короткие выдержки
- полные тексты запрещены

---

## 7) REQUIRED OUTPUT MARKERS (FOR DOWNSTREAM DOCS)
Любой документ, который включает non-user content, обязан хранить рядом:

- KB_SOURCE_RAW: (raw link)
- SOURCE_STATUS: PD_CONFIRMED | LICENSE_CONFIRMED
- SOURCE_NOTE: short
- FULL_TEXT_ALLOWED: (if full text used)

Если документ хранит несколько corpus items:
- каждый item обязан иметь provenance блок.

---

## 8) CHANGE POLICY (LOCK)
Любые изменения статусов/маркеров/границ:
- только PATCH
- обязательно обновить CHANGE_NOTE
- если изменение влияет на доменные CTL/VAL — синхронизировать соответствующие файлы и Validation Matrix.

---

END.
