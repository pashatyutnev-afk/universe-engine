# CTL — READINESS CHECK (BOOT + KB + LINKBASE) (CANON)

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 40_CTL__CONTROLLERS
LEVEL: L1
DOC_TYPE: CTL (CONTROLLER)
ENTITY_TYPE: CONTROLLER
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.READINESS_CHECK.001
OWNER: SYSTEM
ROLE: Pre-run gate controller. Enforces BOOT completion markers, RAW link base compliance, and KB readiness (entrypoint + provenance laws + scope pointers when task consumes KB). Blocks runtime execution when readiness is not provably confirmed.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Rebuilt readiness gate: explicit boot markers + raw link base checks + KB readiness (entrypoint, source lock, scope pointers). Deterministic CTL verdict."
- REASON: "Tasks were attempted without confirmed laws/standards/KB readiness; resulted in navigation mistakes and unverifiable source usage."
- IMPACT: "Runtime only proceeds when boot markers are confirmed; KB-consuming routes cannot start without provenance and KB_SCOPE_RAW."
- CHANGE_ID: UE.CHG.2026-01-20.CTL.READINESS.001

---

## 0) PURPOSE (LAW)
Этот CTL — обязательный pre-run gate.
Он отвечает на вопрос: можно ли начинать выполнение задачи прямо сейчас.

Проверяется:
- BOOT markers confirmed (как требует START)
- RAW link base доступен и используется (no guessing)
- KB readiness подтверждена (entrypoint loaded + source lock law доступен)
- Если задача потребляет KB: присутствует KB_SCOPE_RAW и правила provenance применимы

---

## 1) ABSOLUTE RULES
### 1.1 RAW-only navigation
Использовать только RAW ссылки из:
- ROOT LINK BASE
- сообщения пользователя
Нельзя угадывать пути.

### 1.2 Boot-first
Нельзя выполнять задачу до PASS этого CTL.

### 1.3 Deterministic verdict
CTL обязан вернуть CTL_VERDICT (см. 6).
FAIL блокирует пайплайн.

---

## 2) REQUIRED REFERENCES (RAW)
START_UNIVERSE_ENGINE (runtime laws / boot marker definition)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/01__START_UNIVERSE_ENGINE.md

ROOT LINK BASE (snapshot)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/00__ROOT_INDEX__UNIVERSE_ENGINE.md

KB ENTRYPOINT  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

KB SOURCE LOCK / NO FANTASY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/12__KB_SOURCE_LOCK_NO_FANTASY.md

KB XREF VALIDATION CHECKLIST (for KB-consuming tasks)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/40_RELATION_XREF/25__KB_XREF_VALIDATION_CHECKLIST.md

---

## 3) INPUTS (MINIMUM)
CTL запускается на каждый RUN перед EXECUTION.

Required inputs (from chat context):
- COMMAND: START_UNIVERSE_ENGINE (as marker that runtime mode is active)
- TASK: user request text
- ROOT_LINK_BASE_RAW: raw link to root index file
Optional:
- KB_SCOPE_RAW: raw link(s) to KB module/item (only if task consumes KB)
- OPTIONAL_LINKS: any additional raw links user provided

If TASK missing → FAIL_CLASS: input absent

---

## 4) READINESS CHECKS (DETERMINISTIC)
### CHECK A — ROOT link base present
- ROOT_LINK_BASE_RAW must be present and resolvable
FAIL_CLASS if broken: RAW missing

### CHECK B — BOOT markers confirmed (as defined by START)
Must be explicitly confirmed in the run trace:
- Naming + UID rules loaded
- Doc Control + Index structure loaded
- Entity model loaded
- KB entrypoint loaded

If any missing → FAIL_CLASS: marker not confirmed

### CHECK C — KB entrypoint reachable
- KB ENTRYPOINT raw link present and resolvable
If missing/unreachable → FAIL_CLASS: RAW missing

### CHECK D — KB Source Lock law available
- KB SOURCE LOCK raw link present and resolvable
If missing/unreachable → FAIL_CLASS: RAW missing

### CHECK E — Determine whether task consumes KB
This CTL classifies task as KB-consuming if any is true:
- user explicitly provides KB_SCOPE_RAW, OR
- task mentions: corpus / poet / цитаты / источники / KB module / KB scope / knowledge base usage, OR
- ORC route selected is a KB-consuming route (example: POET_PACK_ORC)

If task is NOT KB-consuming → skip checks F and G.

### CHECK F — KB_SCOPE_RAW required for KB-consuming task
If KB-consuming:
- KB_SCOPE_RAW must be present in inputs
If missing → FAIL_CLASS: input absent

### CHECK G — Provenance readiness for KB-consuming task
If KB-consuming:
- It must be possible to carry provenance markers into outputs:
  - KB_SOURCE_RAW
  - SOURCE_STATUS (PD_CONFIRMED | LICENSE_CONFIRMED)
  - SOURCE_NOTE
This CTL does not validate the specific source content; it validates readiness to enforce the law:
- confirms KB SOURCE LOCK reference is available (Check D)
- requires KB_SCOPE_RAW is present (Check F)
If either missing → FAIL_CLASS: marker not confirmed (if law unavailable) or input absent (if scope missing)

---

## 5) REQUIRED OUTPUT (CTL TRACE)
This CTL must output a trace section that later steps can cite:

- READINESS_ID: UE.CTL.READINESS_CHECK.001
- ROOT_LINK_BASE_RAW: (raw)
- KB_CONSUMPTION: TRUE|FALSE
- KB_SCOPE_RAW: (raw list) or NONE
- BOOT_MARKERS:
  - NAMING_UID: CONFIRMED|MISSING
  - DOC_CONTROL_INDEX: CONFIRMED|MISSING
  - ENTITY_MODEL: CONFIRMED|MISSING
  - KB_ENTRYPOINT: CONFIRMED|MISSING
- VERDICT: PASS|FAIL
- FAIL_CLASS: (if FAIL)
- REQUIRED_FIXES: list

---

## 6) CTL VERDICT FORMAT (REQUIRED)
- CTL_ID: UE.CTL.READINESS_CHECK.001
- TARGET: RUN_START
- VERDICT: PASS | FAIL
- FINDINGS:
  - bullet list
- REQUIRED_FIXES:
  - bullet list (empty if PASS)
- FAIL_CLASS:
  - RAW missing | marker not confirmed | input absent | policy violation
- RETURN_TO:
  - START_UNIVERSE_ENGINE raw link

---

## 7) DEFAULT FAILOVER / RETURN
If FAIL:
- STOP execution immediately
- return to START_UNIVERSE_ENGINE (boot / inputs / linkbase)
RETURN_TO:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/01__START_UNIVERSE_ENGINE.md

---

END.
