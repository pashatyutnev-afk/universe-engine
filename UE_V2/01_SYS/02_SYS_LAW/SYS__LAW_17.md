# LAW_17

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: LAW
UID: UE.V2.LAW.17.SINGLE_ENTRYPOINT_START.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Единая точка запуска рантайма — START. Никаких обходов.

---

## [M] INTENT
Сделать поведение системы детерминированным: один вход, одна загрузка ядра, один способ начать любую задачу.

---

## [M] RULES
1) Любая задача начинается через UE_V2/00_BOOT/00__START.md.
2) START обязан:
   - подцепить BOOT_SEQ
   - подцепить RUNTIME_MANIFEST (MUST_LOAD)
   - подцепить TASK_ROUTER
   - передать управление в NAV_ROOT и PIPE_DEFAULT
3) "Прямые прыжки" в домены/пайпы/сущности без START запрещены.
4) Исключение: READ-ONLY просмотр по RAW допускается, но не считается запуском.
5) Если START недоступен — STOP.

---

## [M] GATES
PASS если:
- каждый прогон имеет TRACE: ENTRYPOINT=START
REWORK если:
- пайпы/сущности вызываются без START
STOP если:
- START missing / input absent
