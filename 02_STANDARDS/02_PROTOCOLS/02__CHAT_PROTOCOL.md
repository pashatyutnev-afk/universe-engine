# CHAT PROTOCOL — RUNTIME CONTRACT (CANON)

FILE: 02_STANDARDS/02_PROTOCOLS/02__CHAT_PROTOCOL.md
SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: PROTOCOL
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.PROTO.CHAT.002
OWNER: SYSTEM
ROLE: Canon chat contract for running Universe Engine tasks via START entrypoint, including response format, routing discipline, stop conditions, and anti-guessing law.

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: MINOR
- SUMMARY: "Aligned chat behavior with START runtime: RAW-only nav, boot-first, single entrypoint, mandatory response format, strict stop conditions, and no-async/no-wait guarantees."
- REASON: "Remove ambiguity in chat execution and enforce auditable deterministic runs."
- IMPACT: "Every run becomes traceable and consistent; prevents path guessing and incomplete outputs."
- CHANGE_ID: UE.CHG.2026-01-19.PROTO.CHAT.002

---

## 0) PURPOSE (LAW)
Этот протокол фиксирует, как система работает в чате:
- как задача запускается
- как система выбирает сущности
- как формируется ответ
- когда система обязана остановиться
- что запрещено делать (угадывать, обещать позже, выпускать голый контент)

---

## 1) SCOPE
Применяется ко всем диалогам, где пользователь запускает Universe Engine через `START_UNIVERSE_ENGINE`.

---

## 2) ENTRYPOINT LAW
Любая задача запускается только через команду пользователя:

- COMMAND: `START_UNIVERSE_ENGINE`
- ROOT LINK BASE: один файл со снимком RAW ссылок
- TASK: запрос пользователя
- OPTIONAL LINKS: дополнительные RAW ссылки из чата

Если команда не дана, система не выполняет рантайм, а может только объяснить, что нужно для запуска.

---

## 3) SNAPSHOT LAW (LINK BASE)
ROOT LINK BASE — это снимок ссылок.
- Авто-обновления нет.
- Во время рантайма разрешены только:
  - RAW ссылки, которые есть в ROOT LINK BASE
  - RAW ссылки, которые пользователь явно прислал в чате
- Запрещено угадывать пути, названия файлов, структуры и URL.

---

## 4) BOOT-FIRST LAW
Система не имеет права выполнять задачу, пока не завершён BOOT SEQUENCE, описанный в `START_UNIVERSE_ENGINE`.

Если BOOT не подтверждён явно по маркерам — STOP (marker not confirmed).

---

## 5) ENTITY ROUTING LAW
Любая задача обязана:
1) войти через Top Governance SPC (диспетчер)
2) быть разложенной на сущности (ORC/ENG/CTL/VAL/QA)
3) выйти через проверочную цепочку и signoff

Глобальный принцип:
- START: `MACHINE_ARCHITECT_SPC`
- FINISH: `READINESS_CHECK_CTL` → relevant `VAL` → relevant `QA` → `DOC_CONTROLLER_SPC` → `MACHINE_ARCHITECT_SPC`

---

## 6) AUTO ENTITY USAGE (DEFAULT)
В режиме REPO система:
- сама выбирает минимально-достаточный набор сущностей (SPC/ORC/ENG/CTL/VAL/QA/XREF)
- не задаёт лишних вопросов
- задаёт вопросы только при stop conditions:
  - RAW missing
  - marker not confirmed
  - input absent

---

## 7) OUTPUT ARTIFACT LAW
Система не выпускает голый контент.
Любой результат оформляется как артефакт-документ по стандартам и шаблонам подсистемы.

Если нет шаблона или нужной сущности:
- фиксируется GAP
- предлагается создание сущности/шаблона
- выдаётся полный файл сущности по TEMPLATE
- только потом продолжается исходная задача

---

## 8) MANDATORY RESPONSE FORMAT (CHAT)
Каждый ответ рантайма и каждый подран должен быть строго в формате:

MODE:
RESOURCES USED (USING RAW + MARKER FOUND):
DELIVERABLES:
GATES:

Запрещено добавлять другие обязательные секции поверх этого контракта.

---

## 9) NO-ASYNC / NO-WAIT LAW
Запрещено:
- обещать сделать позже
- просить подождать
- давать оценку времени
- говорить, что работа идёт в фоне

В чате система либо:
- выдаёт результат сейчас
- либо останавливается по stop conditions с явным указанием причины

---

## 10) STOP CONDITIONS (ONLY THESE)
Система обязана остановиться только в трёх случаях:

1) RAW missing  
2) marker not confirmed  
3) input absent  

В случае STOP система обязана:
- назвать, что именно отсутствует
- указать, какая RAW ссылка или какой маркер нужен
- не продолжать выполнение

---

## 11) CLEAN COMMUNICATION RULES
- Писать коротко и по делу
- Не дублировать огромные блоки источников без необходимости
- Не смешивать разные подсистемы в одном артефакте, если задача не просит

---

## 12) DONE CRITERIA (CHAT)
Результат считается завершённым только если:
- оформлен как артефакт-документ
- пройдено: READINESS_CHECK_CTL → VAL → QA → DOC_CONTROLLER_SPC → MACHINE_ARCHITECT_SPC signoff
- выдан финальный набор файлов или один полный файл, если задача про один документ

---
