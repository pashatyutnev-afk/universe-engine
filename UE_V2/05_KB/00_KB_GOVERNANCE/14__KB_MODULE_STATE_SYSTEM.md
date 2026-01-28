# KB MODULE STATE SYSTEM — UNREAD / READ_ONCE / VERIFIED / DEPRECATED (KB)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/14__KB_MODULE_STATE_SYSTEM.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: SPEC
INDEX_TYPE: MODULE_STATE_SYSTEM (KB)
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPEC.MODULE_STATE.001
OWNER: SYSTEM
ROLE: Define operational states for KB modules, allowed transitions, verification criteria, and rules for Memory-OK usage and deprecation

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB module state system with strict transitions and verification gates; enables memory-safe usage and drift control."
- REASON: "KB must be reliable for entities; state controls readiness and prevents hallucinated recall."
- IMPACT: "Only VERIFIED modules may be used from memory; changes trigger revalidation; deprecated modules are blocked."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STATE.001

---

## 0) PURPOSE (LAW)
Состояния KB модулей нужны для:
- управляемого жизненного цикла знаний,
- безопасного режима памяти (Memory-OK),
- контроля дрейфа и деприкации,
- аудита применимости.

State ≠ doc STATUS.
- STATUS (DRAFT/ACTIVE/DEPRECATED) — статус документа.
- MODULE STATE (UNREAD/READ_ONCE/VERIFIED/DEPRECATED) — операционное состояние пригодности для работы и памяти.

---

## 1) STATES (DEFINITIONS)
### 1.1 UNREAD
**Meaning:** модуль существует, но ещё не использовался/не проверялся.  
**Rules:**
- нельзя использовать по памяти,
- можно использовать только после открытия источника (source-locked).

### 1.2 READ_ONCE
**Meaning:** модуль открыт и применялся ограниченно, но ещё не считается надёжным.  
**Rules:**
- нельзя использовать по памяти,
- допускается повторное применение только source-locked или после повторного открытия.

### 1.3 VERIFIED
**Meaning:** модуль доказал надёжность и может быть использован в Memory-OK режиме.  
**Rules:**
- можно использовать по памяти без искажений смысла,
- любые существенные изменения модуля могут сбросить VERIFIED → READ_ONCE.

### 1.4 DEPRECATED
**Meaning:** модуль устарел и запрещён к использованию.  
**Rules:**
- применять нельзя,
- должен быть replacement PATH (что использовать вместо),
- память запрещена.

---

## 2) ALLOWED TRANSITIONS (STRICT)
### 2.1 Normal transitions
- UNREAD → READ_ONCE (после первого открытия и применения)
- READ_ONCE → VERIFIED (после выполнения verification criteria)
- READ_ONCE → DEPRECATED (если устарел и заменён)
- VERIFIED → DEPRECATED (если устарел и заменён)

### 2.2 Reset transitions (on change)
- VERIFIED → READ_ONCE (если изменился смысл, версия, гейт, пороги или шаблон)
- VERIFIED → READ_ONCE (если обнаружен конфликт или регресс)
- READ_ONCE → UNREAD (не используется; запрещён откат назад — только через переоценку или деприкацию)

---

## 3) VERIFICATION CRITERIA (MANDATORY FOR VERIFIED)
Модуль может стать VERIFIED только если:
1) Он имеет actionable контент (procedure/checklist/rubric/template).
2) Он имеет примеры PASS/FAIL (и EDGE если применимо).
3) Он использовался в реальной работе и не дал противоречий.
4) Он согласован с KB Usage Gate (имеет привязку к проверкам/гейтам, если нужно).
5) Он не конфликтует с другими REQUIRED источниками или конфликт разрешён policy.

Факт перевода в VERIFIED должен быть отражён:
- в CHANGE_NOTE модуля (изменение состояния/версии, если вы так фиксируете),
- и/или в KB_CHANGELOG (рекомендуется как запись).

---

## 4) MEMORY-OK LINK (ABSOLUTE)
Memory-OK разрешён только для:
- VERIFIED

Для UNREAD/READ_ONCE/DEPRECATED:
- Memory-NO (переоткрыть источник или STOP).

---

## 5) CHANGE IMPACT RULE (STRICT)
Если модуль в состоянии VERIFIED изменён:
- он должен быть пересмотрен на предмет сброса в READ_ONCE,
- изменение должно попасть в KB_CHANGELOG,
- если модуль влияет на gate/policy/contract → обязательна impact note.

---

## 6) DEPRECATION RULES (MANDATORY)
Если модуль переводится в DEPRECATED:
- должен быть replacement PATH (что использовать вместо),
- должны быть обновлены карты XREF/Task→Scope/Entity→Scope,
- должны быть обновлены сущности, которые ссылались на старый модуль (KB_SOURCES).

Запрещено:
- DEPRECATED без replacement.

---

## 7) WHERE TO STORE STATE (PRACTICE)
State фиксируется в самом модуле в явном поле:

- `STATE: UNREAD|READ_ONCE|VERIFIED|DEPRECATED`

Рекомендация:
- в master-index для критичных модулей можно также отражать STATE (как operational hint),
  но первичный источник состояния — сам модуль.

---

## 8) QUICK CHECK (FAST)
- Если модуль UNREAD/READ_ONCE → переоткрывать, не вспоминать.
- Если VERIFIED → можно Memory-OK, но без расширения смысла.
- Если DEPRECATED → запрещён, перейти на replacement.

--- END.
