UID & MARKING STANDARD (CANON)

FILE: 02_STANDARDS/01_SPECIFICATIONS/01__UID_AND_MARKING_STANDARD.md
SCOPE: Universe Engine
LAYER: 02_STANDARDS/01_SPECIFICATIONS
DOC_TYPE: STANDARD
STANDARD_TYPE: UID_AND_MARKING
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.STD.UID_MARKING.001
OWNER: SYSTEM
ROLE: Operational standard for applying UID rules and document marking consistently across all layers. Defines enforcement rules, XREF integrity requirements, and machine-friendly marking patterns.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt XREF discipline: no placeholder UID references; added RAW+UID coupling rule; clarified marking blocks and validation checklist; DOC CONTROL body sanitized."
- REASON: "Inconsistent UID references break UID-first navigation and audit. XREF must reference only real IDs or explicit TBD."
- IMPACT: "UID-first becomes reliable; standards can be validated mechanically; fewer broken references."
- CHANGE_ID: UE.CHG.2026-01-20.STD.UIDMARK.001

---

## 0) PURPOSE (LAW)
Этот стандарт описывает **как правильно применять** правила UID и маркировки документов в Universe Engine.

Важно:
- **UID правила задаются в System Law**. Этот документ не переопределяет LAW, а стандартизирует применение и проверку.
- Любая ссылка по UID должна быть **реальной и проверяемой**.

---

## 1) AUTHORITIES (REFERENCE)
### 1.1 UID law authority (SoT)
UID формат и допустимые схемы задаются здесь:
- `01_SYSTEM_LAW/02__UID_RULES.md`
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md

### 1.2 Doc Control authority (SoT)
Обязательные поля, запрет дублирования метаданных, правила шапки:
- `02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md`
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

---

## 2) DEFINITIONS

### 2.1 UID
UID — канонический уникальный идентификатор документа/сущности в системе (UID-first подход).

### 2.2 Marking
Marking — набор стандартных полей/маркеров, которые позволяют:
- машинную валидацию документов,
- устойчивую навигацию,
- аудируемость изменений.

### 2.3 XREF entry
XREF entry — запись “ссылка на сущность/документ” внутри стандарта/индекса/реестра.

---

## 3) UID-FIRST RULES (ABSOLUTE)

### 3.1 UID is the primary identity
- UID — первичная идентичность.
- Имя файла и путь — вторичны, но должны быть согласованы через Doc Control (`FILE:`).

### 3.2 No placeholder UID references (STRICT)
Запрещено писать “примерные” UID в XREF, если они не существуют.

Разрешены только варианты:
- `UID: <real uid from target file header>`
- `UID: TBD` (если документ/сущность ещё не создана)

Любое другое (“UE.LAW.CORE.000” без реально существующего файла) — нарушение.

### 3.3 RAW + UID coupling rule (WHEN NAVIGATION NEEDED)
Если XREF предполагает навигацию (переход/использование), запись должна содержать:
- `UID` (реальный), и
- `RAW` (ссылка), если режим RAW-only активен и ссылку разрешает область

Если область запрещает RAW — оставляем UID-only.

---

## 4) MARKING STANDARD (DOC CONTROL COMPATIBLE)

### 4.1 Header is the only meta location (ABSOLUTE)
- Все поля `STATUS/LOCK/VERSION/UID/OWNER/ROLE/FILE/...` живут **только в header**.
- Нельзя дублировать эти поля в теле документа (никаких “FINAL RULE (LOCK) LOCK: …”).

### 4.2 Minimal marking fields (REQUIRED BY DOC CONTROL)
Для любого контролируемого документа должны быть:
- `FILE`
- `SCOPE`
- `LAYER`
- `DOC_TYPE`
- `LEVEL`
- `STATUS`
- `LOCK`
- `VERSION`
- `UID`
- `OWNER`
- `ROLE`
- `CHANGE_NOTE` (с CHANGE_ID)

(Конкретный список и правила — в Doc Control authority.)

---

## 5) XREF ENTRY FORMAT (CANON)

### 5.1 Canon XREF entry (recommended)
Используй атомарные записи:

- ITEM: "<human readable name>"
  TYPE: <DOC | ENTITY | TEMPLATE | REGISTRY | FOLDER | OTHER>
  UID: <real uid | TBD>
  RAW: <raw link if allowed and needed>
  PATH_LABEL: <optional; human label only>
  NOTES: "<short usage hint>"

Правила:

- `UID` обязателен (реальный или `TBD`).
    
- `RAW` обязателен, если:
    
    - режим RAW-only активен,
        
    - запись предполагает навигацию,
        
    - и правила области разрешают RAW.
        
- `PATH_LABEL` никогда не является механизмом навигации.
    

---

## 6) VALIDATION CHECKLIST (MUST BEFORE COMMIT)

### 6.1 UID integrity

- Каждый `UID` в XREF:
    
    - либо реально существует в заголовке целевого файла,
        
    - либо равен `TBD`.
        

### 6.2 FILE-path integrity

- `FILE:` в целевом документе совпадает с фактическим путём файла.
    

### 6.3 No meta duplication

- В теле документа нет повторов header-меты.
    

### 6.4 RAW-only compliance (if enabled)

- Нет ссылок/путей, которые требуют “угадывания”.
    
- Все переходы — только по RAW из разрешённой базы.
    

---

## 7) EXAMPLES (REFERENCE)

### 7.1 Correct XREF (with RAW)

```yaml
- ITEM: "UID RULES (LAW)"
  TYPE: DOC
  UID: UE.LAW.UID.001
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
  NOTES: "Authority for UID formats and allowed schemas."
```

### 7.2 Correct XREF (UID-only, RAW forbidden)

```yaml
- ITEM: "Some restricted document"
  TYPE: DOC
  UID: UE.SOMETHING.123
  NOTES: "RAW forbidden in this scope; UID-only reference."
```

### 7.3 Correct XREF (TBD)

```yaml
- ITEM: "New standard to be created"
  TYPE: DOC
  UID: TBD
  NOTES: "Create doc first, then replace TBD with real UID + RAW."
```

---

## 8) END