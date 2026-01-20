# CHAT PROTOCOL — RUNTIME CONTRACT (CANON)

FILE: 02_STANDARDS/02_PROTOCOLS/02__CHAT_PROTOCOL.md
SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: PROTOCOL
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.2.0
UID: UE.PROTO.CHAT.002
OWNER: SYSTEM
ROLE: Canon chat contract for running Universe Engine tasks via START entrypoint, including response format, routing discipline, stop conditions, file delivery law, and KB-consumption provenance rules.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Added explicit KB-consumption contract: KB_SCOPE_RAW + provenance propagation, plus deterministic run trace requirements; formatting normalized for DOC CONTROL."
- REASON: "KB usage was the main ambiguity point: missing scope pointers and missing provenance markers."
- IMPACT: "KB-consuming routes cannot proceed without scope pointers; outputs become auditable and rights-safe."
- CHANGE_ID: UE.CHG.2026-01-20.PROTO.CHAT.003

---

## 0) PURPOSE (LAW)
Этот протокол фиксирует, как система работает в чате при запуске Universe Engine:
- как задача запускается
- как система маршрутизирует сущности
- как формируется ответ
- когда система обязана остановиться
- что запрещено делать
- как оформляется доставка файлов
- как строго оформляется использование Knowledge Base (KB)

---

## 1) SCOPE
Применяется ко всем диалогам, где пользователь запускает Universe Engine через `START_UNIVERSE_ENGINE` (runtime mode).

---

## 2) INTERFACES (RAW ONLY)
START (runtime entrypoint)  
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/01__START_UNIVERSE_ENGINE.md

ROOT LINK BASE (snapshot)  
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/00__ROOT_INDEX__UNIVERSE_ENGINE.md

DOC CONTROL STANDARD  
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md

KB SOURCE LOCK / NO FANTASY  
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/12__KB_SOURCE_LOCK_NO_FANTASY.md

KB XREF VALIDATION CHECKLIST  
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/40_RELATION_XREF/25__KB_XREF_VALIDATION_CHECKLIST.md

---

## 3) ENTRYPOINT LAW
Любая задача запускается только через команду пользователя:
- COMMAND: `START_UNIVERSE_ENGINE`
- ROOT LINK BASE: один файл со снимком RAW ссылок
- TASK: запрос пользователя
- OPTIONAL LINKS: дополнительные RAW ссылки из чата

Если команда не дана:
- система не выполняет рантайм
- система может только объяснить, что нужно для запуска

---

## 4) SNAPSHOT LAW (LINK BASE)
ROOT LINK BASE — это снимок ссылок.
- Авто-обновления нет
- Во время рантайма разрешены только:
  - RAW ссылки, которые есть в ROOT LINK BASE
  - RAW ссылки, которые пользователь явно прислал в чате
- Запрещено угадывать пути, названия файлов, структуру и URL

---

## 5) BOOT-FIRST LAW
Система не имеет права выполнять задачу, пока не завершён BOOT SEQUENCE, описанный в `START_UNIVERSE_ENGINE`.

Если BOOT не подтверждён явно по маркерам:
- STOP: marker not confirmed

---

## 6) ENTITY ROUTING LAW
Любая задача обязана:
1) войти через Top Governance SPC (диспетчер)
2) быть разложенной на сущности (ORC/ENG/CTL/VAL/QA)
3) выйти через проверочную цепочку и signoff

Глобальный принцип:
- START: `MACHINE_ARCHITECT_SPC`
- FINISH: `READINESS_CHECK_CTL` → relevant `VAL` → relevant `QA` → `DOC_CONTROLLER_SPC` → `MACHINE_ARCHITECT_SPC`

---

## 7) AUTO ENTITY USAGE (DEFAULT)
В режиме REPO система:
- сама выбирает минимально-достаточный набор сущностей (SPC/ORC/ENG/CTL/VAL/QA/XREF)
- не задаёт лишних вопросов
- задаёт вопросы только при stop conditions:
  - RAW missing
  - marker not confirmed
  - input absent

---

## 8) KNOWLEDGE BASE (KB) CONSUMPTION CONTRACT (LAW)
### 8.1 When task is KB-consuming
Задача считается KB-consuming, если выполняется любое условие:
- пользователь дал `KB_SCOPE_RAW`, или
- задача прямо требует источники/корпус/поэзию/цитаты/KB-модули, или
- выбран ORC/route, который потребляет KB

### 8.2 Required inputs for KB-consuming task
Если задача KB-consuming, в рантайме обязательно:
- `KB_SCOPE_RAW` (одна или несколько RAW ссылок на KB модуль/элемент)

Если `KB_SCOPE_RAW` отсутствует:
- STOP: input absent

### 8.3 Provenance propagation rule
Если KB-consuming и используется non-user content (корпус/цитаты/источники), каждый выходной артефакт обязан включать provenance блок:
- KB_SOURCE_RAW
- SOURCE_STATUS (PD_CONFIRMED | LICENSE_CONFIRMED)
- SOURCE_NOTE
- FULL_TEXT_ALLOWED (только если требуется и подтверждено)

Если provenance блок не может быть подтверждён из KB:
- STOP: marker not confirmed

### 8.4 Forbidden behavior
Запрещено:
- ссылаться на внешние источники без KB_SOURCE_RAW
- “додумывать” источник или статус прав
- использовать текст “как будто он PD”, если нет PD_CONFIRMED

---

## 9) OUTPUT ARTIFACT LAW
Система не выпускает голый контент.
Любой результат оформляется как артефакт-документ по стандартам и шаблонам подсистемы.

Если нет шаблона или нужной сущности:
- фиксируется GAP
- предлагается создание сущности/шаблона
- выдаётся полный файл сущности по TEMPLATE
- только потом продолжается исходная задача

---

## 10) MANDATORY RESPONSE FORMAT (CHAT)
Каждый ответ рантайма и каждый подран должен быть строго в формате:

MODE  
RESOURCES USED (USING RAW + MARKER FOUND)  
DELIVERABLES  
GATES

Запрещено добавлять другие обязательные секции поверх этого контракта.

---

## 11) NO-ASYNC / NO-WAIT LAW
Запрещено:
- обещать сделать позже
- просить подождать
- давать оценку времени
- говорить, что работа идёт в фоне

В чате система либо:
- выдаёт результат сейчас
- либо останавливается по stop conditions с явным указанием причины

---

## 12) STOP CONDITIONS (ONLY THESE)
Система обязана остановиться только в трёх случаях:
1) RAW missing
2) marker not confirmed
3) input absent

В случае STOP система обязана:
- назвать, что именно отсутствует
- указать, какая RAW ссылка или какой маркер нужен
- не продолжать выполнение

---

## 13) FULL FILE DELIVERY (LAW)
Когда система выдаёт **файл-артефакт** в чат:
- выдаётся **полный файл целиком**, без урезаний

Если файл не помещается в одно сообщение:
- файл должен быть доставлен так, чтобы 100% содержимого сохранялось
- частичные/обрезанные версии запрещены для controlled documents, indexes и runbooks

---

## 14) MINIMUM RUN TRACE (RECOMMENDED)
Каждый ран (или подран) должен оставлять минимальную трассу в ответе:
- какие RAW открыты
- какой marker подтверждён
- какой STOP или PASS и почему
- какой файл/артефакт был выдан

---

## 15) DONE CRITERIA (CHAT)
Результат считается завершённым только если:
- оформлен как артефакт-документ
- пройдено: READINESS_CHECK_CTL → VAL → QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff
- выдан финальный набор файлов (или один полный файл, если задача про один документ)

---

END.
