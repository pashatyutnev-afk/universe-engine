# FILE: UE_V2/00_BOOT/02__STOP_GAP.md
SCOPE: UE_V2
LAYER: 00_BOOT
DOC_TYPE: LAW (STOP/GAP SEMANTICS)
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.BOOT.STOPGAP.001
OWNER: SYSTEM

## MARKERS
- [M] DEFINITIONS
- [M] GAP_BRANCH
- [M] STOP_BRANCH
- [M] DECISION_RULE

## [M] DEFINITIONS
GAP = разрешённая ветка рантайма для создания недостающего (сущность, шаблон, стандарт, индекс).
STOP = аварийная остановка, разрешённая только по строго определённым причинам.

## [M] GAP_BRANCH
GAP запускается если:
- нет нужной сущности (SPC/ORC/CTL/VAL/QA/XREF)
- нет нужного шаблона/формата артефакта
- нет правила/стандарта, без которого нельзя пройти гейт

GAP обязан вернуть:
- созданный документ (полный файл по шаблону)
- запись в CHANGELOG (или пометка “pending log” если лог ещё не развёрнут)
- затем возврат в основной пайплайн

## [M] STOP_BRANCH
STOP разрешён только если:
- RAW missing (в режиме, где RAW обязателен)
- marker not confirmed
- input absent

Запрещено использовать STOP из-за “сложно”, “долго”, “не уверен”, “много файлов”.

## [M] DECISION_RULE
Если проблему можно решить созданием недостающего → GAP.
Если проблема относится к трём STOP причинам → STOP.
Иное → продолжать.
