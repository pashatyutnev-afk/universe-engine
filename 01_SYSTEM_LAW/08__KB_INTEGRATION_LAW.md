# KB INTEGRATION LAW (CANON)

FILE: 01_SYSTEM_LAW/08__KB_INTEGRATION_LAW.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.LAW.KB.INTEGRATION.008
OWNER: SYSTEM
ROLE: Declares system-level law for deterministic Knowledge Base (KB) usage. Forces pipeline/gate bindings to KB via KB XREF maps and enforces evidence trace.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "System law: deterministic KB integration through pipeline→scope and gate→dependency maps + mandatory evidence trace."
- REASON: "Prevent KB drift, hidden gate usage, and non-auditable outputs."
- IMPACT: "KB consumption becomes enforceable, reproducible, and audit-ready."
- CHANGE_ID: UE.CHG.2026-01-20.LAW.KB.008

---

## 0) PURPOSE (LAW)
KB является операционным слоем качества и происхождения (provenance).  
Использование KB должно быть детерминированным и проверяемым.

---

## 1) ABSOLUTE KB INTEGRATION LAWS

### L1 — PIPELINE→SCOPE BINDING REQUIRED
Если пайплайн помечен как KB-consuming (TRUE/CONDITIONAL), он обязан иметь явные KB scopes в канонической карте:
- 04_KNOWLEDGE_BASE/40_RELATION_XREF/100__KB_PIPELINE_TO_KB_SCOPE_MAP.md

Если обязательный scope не определён → STOP: marker not confirmed.

---

### L2 — GATE→KB DEPENDENCY BINDING REQUIRED
Любой gate (CTL/VAL/QA), который зависит от KB, обязан иметь явные KB зависимости в канонической карте:
- 04_KNOWLEDGE_BASE/40_RELATION_XREF/101__KB_GATE_TO_MODULE_MAP.md

Если gate KB-dependent, но dependencies не определены → STOP: marker not confirmed.

---

### L3 — EVIDENCE TRACE REQUIRED
Любой output, который потреблял KB, обязан включать evidence trace:
- KB_SCOPE_USED (если scope required)
- KB_SOURCES_USED (если были источники)
- KB_GATES_APPLIED (какие gates реально применены)
- provenance markers, если был non-user content

Эталон trace:
- 04_KNOWLEDGE_BASE/30_SHARED_LIBRARIES/50_EXAMPLES/01__EXAMPLE__KB_CONSUMPTION_TRACE.md

Если trace отсутствует → FAIL (gate violation).

---

### L4 — RAW-ONLY NAVIGATION
Любые KB ссылки в процессе работы должны быть RAW-only и происходить из разрешённой базы ссылок.

---

## 2) ENFORCEMENT (LAW)
- Readiness gate обязан проверять наличие KB_SCOPE_RAW, если пайплайн требует scope.
- Валидаторы обязаны блокировать output без trace, если KB была потреблена.

---

END.
