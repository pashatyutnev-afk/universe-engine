# FILE: UE_V2/00_BOOT/00__START.md
SCOPE: UE_V2
LAYER: 00_BOOT
DOC_TYPE: ENTRYPOINT (RUNBOOK)
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.BOOT.START.001
OWNER: SYSTEM

## MARKERS
- [M] PURPOSE
- [M] MIN_INPUTS
- [M] ABS_LAWS
- [M] BOOT_SEQ_LINK
- [M] RUNTIME_PIPELINE
- [M] OUTPUT_CONTRACT
- [M] STOP_CONDITIONS

## [M] PURPOSE
Единый энтрипоинт рантайма V2. Любая задача начинается здесь.
Запрет обхода: ни один документ не является энтрипоинтом кроме этого.

## [M] MIN_INPUTS
Runtime разрешён только если присутствует:
- COMMAND: START_UNIVERSE_ENGINE
- TASK: текст запроса пользователя
- LINK_BASE: либо ROOT LINK BASE, либо набор RAW ссылок, присланных пользователем

Если LINK_BASE отсутствует, допускается режим V2_LOCAL (без RAW), но только для генерации новых V2-документов внутри UE_V2.

## [M] ABS_LAWS
1) RAW-only: использовать только RAW ссылки, которые прислал пользователь или которые уже подтверждены в текущем рантайме
2) Boot-first: нельзя выполнять задачу до BOOT COMPLETE
3) No guessing: запрещено угадывать пути, роли, ссылки, сущности
4) Minimal entity usage: брать минимально-достаточный набор сущностей
5) Artifact-only: выдавать только оформленные артефакты (документ по стандарту), без “голого контента”
6) GAP duty: если не хватает сущности или шаблона, идти в GAP BRANCH (создать недостающее), затем продолжить
7) STOP строго по STOP_CONDITIONS (ниже)

## [M] BOOT_SEQ_LINK
BOOT порядок описан в: UE_V2/00_BOOT/01__BOOT_SEQ.md

## [M] RUNTIME_PIPELINE
DEFAULT:
- INTAKE → ROUTE → EXEC → CONTROL/VALIDATE → QA → PACKAGE → SIGNOFF

## [M] OUTPUT_CONTRACT
Каждый ответ ассистента обязан содержать секции:
- MODE
- RESOURCES USED (USING RAW + MARKER FOUND)
- DELIVERABLES
- GATES

## [M] STOP_CONDITIONS
STOP разрешён только если:
- RAW missing (нельзя продолжать без ссылок, когда режим не V2_LOCAL)
- marker not confirmed (нет маркера в загруженном документе)
- input absent (нет TASK или COMMAND)
