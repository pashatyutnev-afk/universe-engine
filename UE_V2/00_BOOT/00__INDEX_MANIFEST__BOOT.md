# 00__INDEX_MANIFEST__00_BOOT

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: INDEX_MANIFEST
FOLDER_TAG: UE_V2__00_BOOT
FOLDER_PATH: UE_V2/00_BOOT/
UID: UE.V2.IDX.UE_V2__00_BOOT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
INDEX_SCHEMA: UE_V2.INDEX_MANIFEST.v1
UPDATED_AT: 2026-01-29

---

## [M] PURPOSE
Единая таблица адресов и кратких смыслов для папки `UE_V2/00_BOOT/`.
Используется рантаймом для:
- MUST_LOAD минимального набора
- выдачи адресов по KEY/UID
- подтверждения доступности BOOT-контуров (SEQ/STOP/TRACE/FAIL_CODES/MANIFEST/ROUTER/PROTOCOLS)

---

## [M] RULES
- Этот файл хранит RAW-адреса для объектов этой папки и для ключевых внешних хабов, если они нужны как точки перехода.
- PIPELINE_CONTRACT НЕ хранит RAW, он обращается к объектам через KEY/UID, а адрес берёт отсюда.
- SELF-ENTRY обязателен.
- Допускается хранить внешние “HUB pointers” (NAV_ROOT / PIPE_DEFAULT / LOG_RULES), но только как SHORT_LIST.

---

## [M] LOAD_POLICY (ANTI_NOISE)
ALWAYS_LOAD (если задача касается запуска/роутинга/протоколов):
- SELF
- BOOT_SEQ
- STOP_GAP
- TRACE
- FAIL_CODES
- RUNTIME_MANIFEST
- TASK_ROUTER
- STEP_RUN_PROTOCOL
- FOCUS_LOOP_PROTOCOL
- COMMANDS

NEVER:
- массовая загрузка деревьев
- обход индексов
- загрузка файлов без запроса пайплайна/роутера

---

## [M] LOOKUP (как машина ищет)
LOOKUP_ORDER:
1) KEY
2) UID
3) PATH (только как справка, не для навигации)

REQUIRED_FIELDS_PER_ITEM:
- KEY
- DOC_TYPE
- RAW
- SUMMARY

OPTIONAL_FIELDS:
- UID
- MARKER
- MUST_LOAD
- TAGS
- DEPENDS_ON_KEYS

---

## [M] ITEMS (TABLE OF ADDRESSES)

### SELF
- KEY: SELF
  DOC_TYPE: INDEX_MANIFEST
  UID: UE.V2.IDX.UE_V2__00_BOOT.001
  PATH: UE_V2/00_BOOT/00__INDEX_MANIFEST__UE_V2__00_BOOT.md
  RAW: <PASTE_RAW_HERE>
  MUST_LOAD: true
  SUMMARY: "This index manifest for UE_V2/00_BOOT."

### BOOT SEQUENCE CORE
- KEY: BOOT_SEQ
  DOC_TYPE: BOOT_SEQ
  UID: UE.V2.BOOT.SEQ.001
  PATH: UE_V2/00_BOOT/01__BOOT_SEQ.md
  RAW: <PASTE_RAW_HERE>
  MARKER: "[M] BOOT SEQ"
  MUST_LOAD: true
  SUMMARY: "Canonical boot sequence for runtime start."

- KEY: STOP_GAP
  DOC_TYPE: STOP_GAP
  UID: UE.V2.BOOT.STOPGAP.001
  PATH: UE_V2/00_BOOT/02__STOP_GAP.md
  RAW: <PASTE_RAW_HERE>
  MARKER: "[M] STOP / GAP"
  MUST_LOAD: true
  SUMMARY: "Stop conditions and GAP handling rules."

- KEY: TRACE
  DOC_TYPE: TRACE_RULES
  UID: UE.V2.BOOT.TRACE.001
  PATH: UE_V2/00_BOOT/06__TRACE.md
  RAW: <PASTE_RAW_HERE>
  MARKER: "[M] TRACE"
  MUST_LOAD: true
  SUMMARY: "Trace on/off and trace token format."

- KEY: FAIL_CODES
  DOC_TYPE: FAIL_CODES
  UID: UE.V2.BOOT.FAILCODES.001
  PATH: UE_V2/00_BOOT/07__FAIL_CODES.md
  RAW: <PASTE_RAW_HERE>
  MARKER: "[M] FAIL_CODES"
  MUST_LOAD: true
  SUMMARY: "Canonical error codes for runtime failures."

### ROUTING + MANIFEST
- KEY: RUNTIME_MANIFEST
  DOC_TYPE: RUNTIME_MANIFEST
  UID: UE.V2.BOOT.MANIFEST.001
  PATH: UE_V2/00_BOOT/08__RUNTIME_MANIFEST.md
  RAW: <PASTE_RAW_HERE>
  MARKER: "MUST_LOAD_SET"
  MUST_LOAD: true
  SUMMARY: "Minimal must-load set and core runtime pointers."

- KEY: TASK_ROUTER
  DOC_TYPE: TASK_ROUTER
  UID: UE.V2.BOOT.ROUTER.001
  PATH: UE_V2/00_BOOT/09__TASK_ROUTER.md
  RAW: <PASTE_RAW_HERE>
  MARKER: "ROUTE_TOKEN"
  MUST_LOAD: true
  SUMMARY: "Deterministic routing to DOMAIN/PIPE/IDX/CHECKS."

### STEP-RUN PROTOCOLS
- KEY: STEP_RUN_PROTOCOL
  DOC_TYPE: PROTOCOL
  UID: UE.V2.BOOT.PROTO.STEPRUN.001
  PATH: UE_V2/00_BOOT/10__STEP_RUN_PROTOCOL.md
  RAW: <PASTE_RAW_HERE>
  MUST_LOAD: true
  SUMMARY: "Step-run execution via 'го' with deterministic progression."

- KEY: FOCUS_LOOP_PROTOCOL
  DOC_TYPE: PROTOCOL
  UID: UE.V2.BOOT.PROTO.FOCUSLOOP.001
  PATH: UE_V2/00_BOOT/12__FOCUS_LOOP_PROTOCOL.md
  RAW: <PASTE_RAW_HERE>
  MUST_LOAD: true
  SUMMARY: "Focus loop to avoid restarting entire run; fixes at the error point."

- KEY: COMMANDS
  DOC_TYPE: COMMANDS
  UID: UE.V2.BOOT.COMMANDS.001
  PATH: UE_V2/00_BOOT/13__COMMANDS.md
  RAW: <PASTE_RAW_HERE>
  MUST_LOAD: true
  SUMMARY: "Runtime command set: go/stop/gap/patch/retry/etc."

---

## [M] HUB POINTERS (SHORT_LIST)
(Разрешённый минимум внешних переходов, если нужны для запуска)

- KEY: NAV_ROOT
  DOC_TYPE: NAV_ROOT
  PATH: UE_V2/04_NAV/00__NAV_ROOT.md
  RAW: <PASTE_RAW_HERE>
  SUMMARY: "Entry for navigation rules + index access confirmation."

- KEY: PIPE_DEFAULT
  DOC_TYPE: PIPE
  PATH: UE_V2/06_PIPE/01__PIPE_DEFAULT.md
  RAW: <PASTE_RAW_HERE>
  SUMMARY: "Default pipeline that hands off to domain pipes."

- KEY: LOG_RULES
  DOC_TYPE: LOG_RULES
  PATH: UE_V2/12_LOG/00__LOG_RULES.md
  RAW: <PASTE_RAW_HERE>
  SUMMARY: "Logging rules and required log panels."

---

## [M] QUICK CHECKS (what must be confirmable through RAW)
- Can open SELF, BOOT_SEQ, STOP_GAP, TRACE, FAIL_CODES, RUNTIME_MANIFEST, TASK_ROUTER, STEP_RUN_PROTOCOL, FOCUS_LOOP_PROTOCOL, COMMANDS.
- If any MUST_LOAD RAW missing -> STOP.
- If marker missing in MUST_LOAD -> STOP (marker not confirmed).
- HUB pointers missing -> GAP (если они нужны по ROUTE_TOKEN).

---

## [M] CHANGELOG
- 2026-01-29: Created initial canonical INDEX_MANIFEST template for UE_V2__00_BOOT.
