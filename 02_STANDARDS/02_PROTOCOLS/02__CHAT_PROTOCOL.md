# CHAT PROTOCOL (STANDARDS)

FILE: 02_STANDARDS/02_PROTOCOLS/02__CHAT_PROTOCOL.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
DOC_TYPE: PROTOCOL (CHAT)
LAYER: 02_STANDARDS
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.PROTO.STD.CHAT.001
OWNER: SYSTEM
ROLE: Operational chat protocol for producing canonical repository artifacts via chat: strict file-by-file delivery, RAW-only navigation, boot-first discipline, gates, and stop conditions.

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: MINOR
- SUMMARY: "Aligned chat protocol with START runtime contract: RAW snapshot navigation, boot-first markers, mandatory run output format, and stop conditions."
- REASON: "Remove ambiguity and enforce auditable deterministic work: one step = one file."
- IMPACT: "Every run is traceable; no guessing; no partial artifacts; no execution before boot markers."
- CHANGE_ID: UE.CHG.2026-01-19.CHAT.001

---

## 0) PURPOSE (LAW)
Этот протокол задаёт **как мы работаем в чате**, чтобы выпускать канонические файлы и артефакты без хаоса:
- строго file-by-file,
- строго по RAW-навигации,
- строго через BOOT дисциплину (когда это требуется),
- строго с гейтами и стоп-условиями,
- строго с выпуском результата как **документ-артефакт** (не “голый контент”).

---

## 1) WORK UNIT (HARD RULE)
Единица работы — **один файл за один шаг**.

### 1.1 Формат шага (обязательный)
Каждый шаг (каждый ответ ассистента, где производится канон) обязан иметь структуру:

- MODE:
- RESOURCES USED (USING RAW + MARKER FOUND):
- DELIVERABLES:
  - полный контент **ОДНОГО** файла (готов к вставке в репозиторий)
- GATES:

### 1.2 Запрещено (жёстко)
- править 10 файлов одним сообщением
- выдавать “кусочки” вместо полного файла
- утверждать, что файл “прочитан/обновлён”, если RAW не был открыт

---

## 2) ENTRYPOINT & TASK START (LAW)
### 2.1 Единственный запуск задач
Любая “задача системы” (не просто перепечатка текста) запускается **только** через команду пользователя:
- `START_UNIVERSE_ENGINE`

ROOT-INDEX — это база RAW-ссылок (снимок), он сам по себе задач не выполняет.

### 2.2 Если пользователь НЕ запускал START
Если пользователь просто просит “переписать/исправить файл X”, допускается:
- работать file-by-file,
- но **без** заявлений “система загрузилась/boot пройден”, пока не было явного boot-run.

---

## 3) NAVIGATION (RAW-ONLY) + SNAPSHOT REFRESH (LAW)
### 3.1 Источник истины по ссылкам
Если пользователь дал **ROOT LINK BASE** (index со снимком RAW-ссылок), то:
- это **единственный** навигационный авторитет для текущей сессии,
- ассистент использует **только** RAW-ссылки из:
  1) ROOT LINK BASE, или
  2) сообщений пользователя.

### 3.2 Snapshot rule
ROOT LINK BASE — **снимок**. Он **не обновляется автоматически**.

### 3.3 Manual refresh rule
Обновление ссылок происходит **только по просьбе пользователя**:
- пользователь вручную присылает новый ROOT-INDEX (или новые RAW-ссылки).
До этого момента:
- набор ссылок считается фиксированным.

### 3.4 NO GUESSING (absolute)
Запрещено:
- угадывать пути/URL,
- “восстанавливать” отсутствующие ссылки,
- ссылаться на “индексы в индексе”, если RAW не подтверждён пользователем.

---

## 4) BOOT-FIRST DISCIPLINE (WHEN RUNNING SYSTEM)
Если задача запущена через `START_UNIVERSE_ENGINE`, то **до выполнения задачи** обязателен BOOT SEQUENCE согласно START-файлу.

### 4.1 Boot markers (must confirm)
BOOT считается завершённым только если явно подтверждено:
- Naming + UID rules loaded
- Doc Control + Index structure loaded
- Entity model loaded
- KB entrypoint loaded

Если любой пункт не подтверждён:
- STOP: `marker not confirmed`

---

## 5) CANON BUILD FLOW (DEFAULT)
### 5.1 Нормальный порядок сборки канона
1) LAW слой (законы и ограничения)
2) STANDARDS слой (форматы, протоколы, doc control)
3) SYSTEM ENTITIES (SPC/ORC/ENG/CTL/VAL/QA/XREF + шаблоны/реестры)
4) KNOWLEDGE BASE (вход + правила + карты)
5) PROJECTS / ASSETS / DATABASES / LOGS (по мере необходимости)

### 5.2 Правило “сначала каркас, потом контент”
Сначала всегда нормализуем:
- naming (`NN__...`)
- Doc Control (шапка, UID, SemVer, LOCK/STATUS)
- индексы/карты хранения/реестры
И только потом:
- движки/спецы/контентные артефакты.

---

## 6) OUTPUT ARTIFACT RULE (HARD)
Система не выпускает “голый контент”.
Любой результат оформляется как **документ-артефакт** по шаблонам и стандартам подсистемы:
- трек → TRACK CARD / PROMPT / RELEASE / OUTPUT PACK (по music standards)
- правило/протокол → стандартный документ с Doc Control + UID + SemVer
- сущность → файл сущности по TEMPLATE соответствующего класса

Если подходящего шаблона/сущности нет:
- сначала GAP → предложение создания → полный файл сущности по TEMPLATE
- только потом продолжение исходной задачи

---

## 7) QUALITY MINIMUM (GATES)
Каждый канонический файл обязан:
- иметь Doc Control шапку (FILE/SCOPE/DOC_TYPE/STATUS/LOCK/VERSION/UID/OWNER/ROLE)
- иметь SemVer `X.Y.Z`
- иметь UID
- не иметь дублей метаданных внизу файла
- иметь ясное назначение (ROLE) и границы (что делает / чего не делает)

---

## 8) CHANGE & LOCK RULE
Если файл объявлен каноном:
- `STATUS: ACTIVE`
- `LOCK: FIXED`

Дальнейшие правки:
- только через Change Management Protocol (и через file-by-file шаги).

---

## 9) USER COMMANDS (OPERATIONAL)
Допустимые команды в чате:
- `го` — продолжить по текущему плану (следующий файл)
- `стоп` — остановить и показать “где мы”
- `откат` — вернуть последний файл к предыдущей версии (через change/alias правила)
- `START_UNIVERSE_ENGINE` — запустить системный рантайм (с BOOT-first)
- `REFRESH_ROOT_INDEX` — пользователь прислал обновлённый ROOT-INDEX (снимок ссылок обновлён вручную)

---

## 10) STOP CONDITIONS (ONLY THESE)
Остановка допускается только по причинам:
- RAW missing
- marker not confirmed
- input absent

---

## FINAL RULE (LOCK)
Один шаг = один файл.
Только так строится канон без хаоса.

--- END.
