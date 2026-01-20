# READINESS CHECK CONTROLLER (CANON)

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 40_CTL__CONTROLLERS
LEVEL: L2
DOC_TYPE: CTL (CONTROLLER)
ENTITY_TYPE: CONTROLLER
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.READINESS_CHECK.001
OWNER: SYSTEM
ROLE: Mandatory readiness gate before execution and before final packaging. Enforces boot-first + inputs present + KB scope trace discipline.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Restored READINESS_CHECK_CTL as a real CTL controller (was misfiled ruleset). Added deterministic readiness checkpoints aligned with START."
- REASON: "START requires READINESS_CHECK_CTL in the finish chain for every run; controller must exist and provide PASS/FAIL."
- IMPACT: "Runtime becomes deterministic: no task proceeds without confirmed BOOT + inputs + KB scope trace markers."
- CHANGE_ID: UE.CHG.2026-01-20.READINESS.001

---

## 0) PURPOSE (LAW)
Этот контроллер — обязательный гейт готовности.
- Он не выполняет задачу по существу.
- Он решает только одно: **PASS или FAIL** готовность рантайма к выполнению и выпуску артефакта.
- Если FAIL — ран останавливается по разрешённым STOP-условиям.

---

## 1) ABSOLUTE LAWS (INHERITED)
### 1.1 Stop conditions (only these)
Разрешённые STOP-условия:
- RAW missing
- marker not confirmed
- input absent

### 1.2 RAW-only navigation
Использовать только RAW ссылки:
- из ROOT LINK BASE, или
- явно присланные пользователем в сообщении.

### 1.3 Boot-first
Нельзя продолжать выполнение задачи, пока BOOT COMPLETE MARKER не подтверждён.

### 1.4 Output artifact rule
Любой результат должен быть оформлен как артефакт-документ по стандартам.
Голый контент запрещён.

---

## 2) CONTROLLER MINI-CONTRACT
### 2.1 CONSUMES
- START command context: `START_UNIVERSE_ENGINE`
- ROOT LINK BASE snapshot (RAW)
- TASK (текст запроса пользователя)
- OPTIONAL LINKS (RAW ссылки пользователя)
- BOOT STATUS (подтверждение 5.5 из START)

### 2.2 PRODUCES
- READINESS_VERDICT: PASS | FAIL
- FAIL_REASON: one of {RAW missing, marker not confirmed, input absent}
- CHECK_REPORT: список результатов проверок (минимальный trace)

### 2.3 DEPENDS_ON (RAW)
- START_UNIVERSE_ENGINE (entrypoint):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/01__START_UNIVERSE_ENGINE.md
- ROOT LINK BASE (snapshot):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/00__ROOT_INDEX__UNIVERSE_ENGINE.md

---

## 3) CHECKPOINTS (DETERMINISTIC)
Контроллер выполняет проверки строго по порядку.
Первая же критическая неудача = FAIL и STOP.

### CHECKPOINT C1 — INPUTS_PRESENT
**Цель:** убедиться, что есть минимальные входы, иначе STOP: input absent.

**REQUIREMENTS:**
- COMMAND = START_UNIVERSE_ENGINE (есть контекст запуска)
- ROOT LINK BASE (RAW) присутствует
- TASK (текст запроса пользователя) присутствует

**FAIL RULE:**
- если отсутствует TASK → FAIL: input absent
- если отсутствует ROOT LINK BASE RAW → FAIL: RAW missing

---

### CHECKPOINT C2 — BOOT_COMPLETE_MARKER_CONFIRMED
**Цель:** убедиться, что BOOT COMPLETE MARKER подтверждён (как в START 5.5), иначе STOP: marker not confirmed.

**REQUIREMENTS (ALL MUST BE CONFIRMED):**
- Naming + UID rules loaded
- Doc Control + Index structure loaded
- Entity model loaded
- KB entrypoint loaded

**FAIL RULE:**
- если любой из 4 пунктов не подтверждён → FAIL: marker not confirmed

---

### CHECKPOINT C3 — RAW_SCOPE_COMPLIANCE
**Цель:** убедиться, что ран не выходит за пределы RAW snapshot.

**REQUIREMENTS:**
- Все используемые RAW ссылки либо:
  - присутствуют в ROOT LINK BASE, либо
  - были явно присланы пользователем.

**FAIL RULE:**
- если встречена ссылка/путь, который не входит в допустимые источники → FAIL: RAW missing  
  (это трактуется как "нет разрешённого RAW на нужный ресурс")

---

### CHECKPOINT C4 — KB_SCOPE_TRACE_MINIMUM
**Цель:** минимально проверить, что KB реально применяется, а не "для вида".

**REQUIREMENTS (MINIMUM TRACE):**
- В ран-отчёте должен быть указан:
  - KB_SCOPE (одно значение)
  - KB_ENTRYPOINT_USED = true (или ссылка на KB master index)
- Если ран заявляет, что применяет знания:
  - должен быть список KB_MODULES_LOADED (минимум 1) или KB_SOURCES_TRACE (минимум 1)

**FAIL RULE:**
- если задача явно требует знаний/методов (любой не-тривиальный output), но KB_SCOPE/trace отсутствуют → FAIL: marker not confirmed

---

### CHECKPOINT C5 — ARTIFACT_READINESS_MINIMUM
**Цель:** предотвратить выпуск "голого контента".

**REQUIREMENTS:**
- Для любого результата должен быть определён:
  - ARTIFACT_TYPE (какой документ выпускаем)
  - OUTPUT_TARGET (куда кладём)
  - DOC CONTROL поля (минимальный набор: FILE/SCOPE/SERIAL/LAYER/DOC_TYPE/STATUS/LOCK/VERSION/UID/OWNER)

**FAIL RULE:**
- если результат не может быть оформлен как документ-артефакт → FAIL: marker not confirmed

---

## 4) VERDICT LOGIC
### 4.1 PASS
PASS возможен только если:
- C1 PASS
- C2 PASS
- C3 PASS
- C4 PASS
- C5 PASS

### 4.2 FAIL
FAIL фиксируется только с одной из причин:
- RAW missing
- marker not confirmed
- input absent

---

## 5) OUTPUT (RUN TRACE MIN)
Контроллер всегда отдаёт минимальный отчёт:

READINESS_VERDICT:
FAIL_REASON:
CHECK_REPORT:
- C1: PASS|FAIL
- C2: PASS|FAIL
- C3: PASS|FAIL
- C4: PASS|FAIL
- C5: PASS|FAIL

---

## 6) NOTES (NON-EXECUTION)
Этот контроллер не подменяет:
- VAL (проверки соответствия)
- QA (качество/гейты)
- DOC_CONTROLLER_SPC (док-контроль)
Он только гарантирует, что запуск и выпуск артефактов возможны по законам START.
