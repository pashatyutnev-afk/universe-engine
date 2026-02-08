# 07__FAIL_CODES

SCOPE: UE_V2  
DOC_TYPE: FAIL_CODES (RUNTIME)  
UID: UE.V2.BOOT.FAILCODES.001  
VERSION: 1.1.0  
STATUS: ACTIVE  
MODE: REPO (USAGE-ONLY, NO-EDIT)  
NAV_RULE: RAW only  
PURPOSE: Единый справочник STOP/GAP/FAIL кодов рантайма. Нужен для детерминированных остановок, коротких сообщений и быстрого ремонта документации/маркерных блоков.

---

## [M] DEFINITIONS
- STOP: рантайм обязан остановиться. Дальше нельзя продолжать без исправления.
- GAP: рантайм может продолжать только в “ограниченном режиме” или требует догрузки/создания недостающего обязательного узла.
- FAIL: ошибка шага/артефакта внутри пайплайна (может быть исправлена в рамках текущего прогона или требует возврата на шаг).

---

## [M] CODE FORMAT
Код пишется так:
- STOP_XX__NAME
- GAP_XX__NAME
- FAIL_XX__NAME

Где:
- XX: двухзначный номер (01..99)
- NAME: короткое имя в UPPER_SNAKE_CASE

---

## [M] CANON STOP CODES (BOOT / NAV / MUST_LOAD)

### STOP_01__TASK_TEXT_MISSING
WHEN:
- В ENTRYPOINT нет TASK_TEXT (задача не задана)
EVIDENCE:
- E0_ENTRYPOINT.TASK_PRESENT = no
ACTION:
- Пользователь должен дать TASK_TEXT (1 строкой, без справки)

---

### STOP_02__RAW_MISSING_MUST_LOAD
WHEN:
- Не удалось открыть RAW для любого MUST_LOAD файла из BOOT SEQ / RUNTIME_MANIFEST / ROUTER / NAV_ROOT / PIPE_DEFAULT / LOG_RULES
EVIDENCE:
- E1_BOOT_LOAD.MUST_LOAD_OPENED содержит “missing”
ACTION:
- Исправить PATH→RAW в ROOT_LINK_BASE или вернуть файл в репу

---

### STOP_03__MARKER_NOT_CONFIRMED_MUST_LOAD
WHEN:
- MUST_LOAD файл открылся, но обязательный [M] marker блок отсутствует/не совпадает
EVIDENCE:
- E1_BOOT_LOAD.MUST_LOAD_MARKERS = missing
ACTION:
- Добавить/восстановить [M] секции в нужном документе

---

### STOP_04__ROUTER_FAILED_ROUTE_TOKEN
WHEN:
- TASK_ROUTER не смог сформировать ROUTE_TOKEN (пустые/невалидные поля)
EVIDENCE:
- ROUTE_TOKEN отсутствует или содержит пустые обязательные поля: DOMAIN/ARTIFACT_TYPE/MODE/PIPE_SELECTED/REQUIRED_IDX
ACTION:
- Исправить правила в TASK_ROUTER или добавить доменный маппинг/дефолты

---

### STOP_05__NAV_REQUIRED_IDX_MISSING
WHEN:
- REQUIRED_IDX из ROUTE_TOKEN не найден/не открывается по RAW
EVIDENCE:
- E3_NAV_CONFIRM.REQUIRED_IDX_OPENED = missing
ACTION:
- Создать/добавить индекс или поправить ссылку/роутинг

---

### STOP_06__NAV_ROOT_MISSING
WHEN:
- UE_V2/04_NAV/00__NAV_ROOT.md отсутствует или не открывается
EVIDENCE:
- E3_NAV_CONFIRM.NAV_ROOT_OPENED = missing
ACTION:
- Восстановить NAV_ROOT и его marker секции

---

### STOP_07__PIPE_DEFAULT_MISSING
WHEN:
- UE_V2/06_PIPE/01__PIPE_DEFAULT.md отсутствует/не открывается
EVIDENCE:
- E4_PIPE_HANDOFF.PIPE_DEFAULT_OPENED = missing
ACTION:
- Восстановить PIPE_DEFAULT (минимальный роутер пайпов)

---

### STOP_08__LOG_RULES_MISSING
WHEN:
- UE_V2/12_LOG/00__LOG_RULES.md отсутствует/не открывается
EVIDENCE:
- E5_LOG_INIT.LOG_RULES_OPENED = missing
ACTION:
- Восстановить LOG_RULES

---

## [M] CANON GAP CODES (MISSING DOMAIN / ENTITIES / PANELS)

### GAP_01__DOMAIN_PIPE_MISSING
WHEN:
- ROUTE_TOKEN.PIPE_SELECTED указывает на доменный PIPE, но он отсутствует/не открывается
ALLOWED:
- продолжать только через PIPE_DEFAULT (если он умеет фолбэк)
BLOCKED:
- доменные шаги/проверки
ACTION:
- добавить доменный PIPE или прописать фолбэк маршрут

---

### GAP_02__DOMAIN_IDX_INCOMPLETE
WHEN:
- REQUIRED_IDX открылся, но не подтверждает доступ к REG/XREF/KB/PIPE/LOG (нет ссылок/панелей)
ALLOWED:
- ограниченный прогон (только общие правила/шаблоны)
BLOCKED:
- полноценная валидация и релизные гейты
ACTION:
- довести доменный IDX до требований NAV_CONFIRM

---

### GAP_03__REQUIRED_CHECKS_MISSING
WHEN:
- REQUIRED_CHECKS из ROUTE_TOKEN не существует (нет файлов чеков или протоколов)
ALLOWED:
- черновой/FAST режим
BLOCKED:
- RELEASE_READY / SIGNOFF
ACTION:
- добавить недостающие проверки или заменить на существующие

---

### GAP_04__DEFAULT_ORC_UNRESOLVED
WHEN:
- DEFAULT_ORC задан, но сущность/файл ORC не найден
ALLOWED:
- работа без оркестратора (ручная последовательность шагов)
BLOCKED:
- автоматическая декомпозиция/распределение задач
ACTION:
- создать ORC или поправить маппинг в ROUTER

---

### GAP_05__REG_OR_XREF_KB_LINKS_MISSING
WHEN:
- IDX не подтверждает доступ к REG/XREF/KB (нет обязательных ссылок)
ALLOWED:
- только PIPE без привязок к REG/XREF/KB
BLOCKED:
- соблюдение канона, трасса полноты
ACTION:
- добавить панели/ссылки в IDX или NAV_ROOT

---

## [M] PIPE FAIL CODES (STEP-RUN / ARTIFACT)

### FAIL_01__STEP_OUTPUT_EMPTY
WHEN:
- Шаг выполнен, но deliverable пустой/не создан
ACTION:
- повторить шаг с уточнением target файла/шаблона

---

### FAIL_02__ARTIFACT_FORMAT_VIOLATION
WHEN:
- Выход не соответствует формату пайпа/шаблона (например нет заголовков, UID, VERSION, [M])
ACTION:
- привести к шаблону домена/пайпа

---

### FAIL_03__QA_GATE_FAILED
WHEN:
- QA/VAL чек не пройден (по рубрике/гейту)
ACTION:
- исправить конкретные пункты чеклиста, затем перепройти gate

---

### FAIL_04__NON_DETERMINISTIC_ROUTE
WHEN:
- При одинаковом входе меняется ROUTE_TOKEN/PIPE без причины
ACTION:
- ужесточить правила ROUTER, убрать случайность, добавить приоритеты

---

### FAIL_05__CONTEXT_NOISE_OVERLOAD
WHEN:
- Нарушена ANTI_NOISE_LOAD_POLICY (слишком много файлов/объяснений)
ACTION:
- откатить до MUST_LOAD + 1 IDX + 1–3 target файла

---

## [M] REQUIRED TRACE FIELDS ON ANY STOP/GAP/FAIL
При любом STOP/GAP/FAIL обязателен блок:

- CODE:
- WHERE: (S0/S1/S2/S3/S4/S5/S6 + event)
- MISSING: (что отсутствует)
- IMPACT: (что блокируется)
- NEXT: (1 действие)

---

## [M] DEFAULT BEHAVIOR
- При STOP: не продолжаем пайп, не “угадываем”, не обходим IDX.
- При GAP: продолжаем только если PIPE_DEFAULT допускает фолбэк и это явно указано.
- При FAIL: возвращаемся на шаг, исправляем, повторяем gate.

---

## [M] EXTENSION POLICY
Добавлять новые коды можно, но:
- не менять значения существующих кодов
- не переиспользовать номера
- поддерживать краткость: 1–3 строки на WHEN/EVIDENCE/ACTION

