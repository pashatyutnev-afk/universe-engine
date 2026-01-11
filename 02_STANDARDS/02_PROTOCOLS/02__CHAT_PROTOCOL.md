# CHAT PROTOCOL (STANDARDS)
FILE: 02_STANDARDS/02_PROTOCOLS/02__CHAT_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: PROTOCOL
INDEX_TYPE: OPERATIONAL
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.PROTO.STD.CHAT.001
OWNER: SYSTEM
ROLE: Operational chat protocol: how we create, revise, validate, and lock canonical documents through chat iterations

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Протокол переписан: минимальный, строгий, под каноническую сборку документов по одному файлу"
- REASON: "Чтобы не было хаоса и '5 пальцев в рот' — работаем file-by-file"
- IMPACT: "Стандартизирует производство канона через диалог"

---

## 0) PURPOSE
Этот протокол задаёт **как мы работаем в чате**, чтобы выпускать канонические файлы без глюков.

---

## 1) WORK UNIT (HARD RULE)
Единица работы — **один файл за шаг**.

Формат шага:
- `FILE N/∞`
- `PATH`
- полный контент файла (готовый к вставке)
- затем следующий файл

Запрещено:
- править 10 файлов одним сообщением
- давать “кусочки без файла”

---

## 2) CANON BUILD FLOW (MANDATORY)
1) Выбираем слой (LAW / STANDARDS / ENTITIES / KB / PROJECTS / ASSETS).
2) Начинаем с entrypoint:
   - master-index
   - doc-registry
3) Затем нормализуем подслои:
   - naming (`NN__`)
   - Doc Control (шапка/UID/SemVer)
   - alias-pointer для миграций
4) Только после этого трогаем содержимое/движки/спецов.

---

## 3) OUTPUT QUALITY (MINIMUM)
Каждый канонический файл обязан:
- иметь Doc Control шапку
- иметь SemVer `X.Y.Z`
- иметь UID
- не иметь дублей OWNER/LOCK/VERSION внизу
- иметь понятную ROLE/назначение

---

## 4) USER COMMANDS (SHORT SET)
В рамках протокола принимаются команды:
- `го` — продолжить по текущему плану
- `стоп` — остановить и показать “где мы”
- `откат` — вернуть последний файл к предыдущей версии (через alias/версии)

---

## 5) LOCK RULE
Если файл объявлен каноном:
- `STATUS: ACTIVE`
- `LOCK: FIXED`
Дальше правки только через Change Management Protocol.

---
## AI NAVIGATION PROTOCOL (OPERATIONAL)
### A) Link Source of Truth
- If user provides a link library (index or pasted subset), it becomes the ONLY navigation authority for the session.
- Assistant must not guess or construct repository links.

### B) Subset Mode
- If only part of an index is pasted, assistant must treat it as the full operational universe for this chat.

### C) Verification Rule
- Assistant must quote exact RAW URL before stating file state (empty/filled) or proposing rewrite.

## FINAL RULE (LOCK)
Один шаг = один файл. Только так строится канон без хаоса.
--- END.
