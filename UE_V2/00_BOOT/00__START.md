# 00__START

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: BOOT / ENTRYPOINT
UID: UE.V2.BOOT.START.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Единая точка запуска рантайма. Запрещает обходы. Поднимает ядро и передаёт управление пайплайну.

---

## [M] INTENT
Запустить работу системы так, чтобы она:
- не прошла мимо REG/XREF/KB/PIPE/NAV/LOG
- не засорила контекст
- могла работать пошагово через "го"
- выбирала путь детерминированно через ROUTER

---

## [M] MIN_INPUTS
- TASK_TEXT (что нужно сделать)
- OPTIONAL: MODE_HINT (FAST|RELEASE_READY|MASTERPIECE)
- OPTIONAL: constraints (platform, duration, style, references)

---

## [M] START_SEQUENCE (CANON)
S0) ENTRYPOINT CHECK
- подтвердить, что это запуск задачи (есть TASK_TEXT)

S1) BOOT SEQ
- открыть: UE_V2/00_BOOT/01__BOOT_SEQ.md
- применить: UE_V2/00_BOOT/02__STOP_GAP.md
- включить трассу: UE_V2/00_BOOT/06__TRACE.md
- включить коды ошибок: UE_V2/00_BOOT/07__FAIL_CODES.md

S2) MUST_LOAD ядро
- открыть: UE_V2/00_BOOT/08__RUNTIME_MANIFEST.md
- подхватить MUST_LOAD_SET (только минимум)

S3) ROUTING
- открыть: UE_V2/00_BOOT/09__TASK_ROUTER.md
- сформировать ROUTE_TOKEN:
  DOMAIN, ARTIFACT_TYPE, MODE, PIPE_SELECTED, DEFAULT_ORC, REQUIRED_IDX, REQUIRED_CHECKS, EXEC_MODE

S4) NAV
- открыть: UE_V2/04_NAV/00__NAV_ROOT.md
- открыть IDX из ROUTE_TOKEN (REQUIRED_IDX)
- подтвердить доступ к REG/XREF/KB/PIPE/LOG через IDX

S5) PIPE EXEC (STEP-RUN)
- открыть: UE_V2/06_PIPE/01__PIPE_DEFAULT.md
- если ROUTE_TOKEN.PIPE_SELECTED доменный -> handoff в него (через PIPE_DEFAULT routing)
- включить протоколы:
  - UE_V2/00_BOOT/10__STEP_RUN_PROTOCOL.md
  - UE_V2/00_BOOT/12__FOCUS_LOOP_PROTOCOL.md
  - UE_V2/00_BOOT/13__COMMANDS.md

S6) LOG INIT
- открыть: UE_V2/12_LOG/00__LOG_RULES.md
- подтвердить, что доступны:
  - UE_V2/12_LOG/01__RUN_LOG.md
  - UE_V2/12_LOG/03__TOKEN_ARCHIVE.md
  - UE_V2/12_LOG/04__DECISION_LOG.md

---

## [M] ANTI_NOISE_LOAD_POLICY
- ALWAYS: START + MANIFEST + ROUTER + NAV_ROOT
- THEN: один доменный IDX + 1–3 target файла
- NEVER: обход IDX и массовая загрузка деревьев
- OUTPUT-FIRST: максимум контекста отдаётся под контент/результат, не под справку

---

## [M] STOP / GAP
STOP только если:
- RAW missing для MUST_LOAD
- marker not confirmed для MUST_LOAD
- input absent (нет задачи)

GAP если:
- отсутствует доменный PIPE/IDX/обязательная сущность/панель по ROUTE_TOKEN

---

## [M] OUTPUT (START TOKEN)
START_OUTPUT:
- ROUTE_TOKEN (обязателен)
- FIRST_STEP_PROMPT: "го"

---

## [M] GATES
PASS если:
- ROUTE_TOKEN сформирован
- MUST_LOAD доступен
- NAV_ROOT доступен
- PIPE_DEFAULT доступен
STOP если:
- нет TASK_TEXT
- MUST_LOAD missing
GAP если:
- отсутствует доменный пайп/индекс/обязательные проверки

Ссылка для запуска системы: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/00__INDEX_MANIFEST__UE_V2.md