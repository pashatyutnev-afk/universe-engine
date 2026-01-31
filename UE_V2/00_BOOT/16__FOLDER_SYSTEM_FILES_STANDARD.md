SCOPE: Universe Engine (UE_V2)
DOC_TYPE: LAW / STANDARD
UID: UE.V2.LAW.FOLDER.SYSTEM_FILES.016
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only

---

## [M] PURPOSE
Стандартизировать системные файлы на уровне каждой папки, чтобы:
- навигация была детерминированной
- адреса жили в одном месте
- процесс исполнения жил в другом месте
- не плодились README/manifest-двойники без смысла

---

## [M] CANON: REQUIRED FILES PER FOLDER
Каждая “рабочая” папка UE_V2 обязана иметь ровно два системных файла:

1) 00__<FOLDER>__INDEX_MANIFEST.md
- роль: адресная книга (KEY → RAW + краткий смысл + мета)
- RAW: разрешён
- аудит: наличие всех ключевых объектов папки

2) 00__<FOLDER>__PIPELINE_CONTRACT.md
- роль: контракт действий (steps/roles/tokens), работает только по KEY
- RAW: запрещён
- аудит: все REQUIRED_KEYS резолвятся через INDEX_MANIFEST

---

## [M] OPTIONAL: START NODE (LOCAL ENTRY)
Если папка должна быть “локальной старт-точкой”, добавляется третий файл:

3) 00__<FOLDER>__START_NODE.md
- роль: быстрый старт домена/секции “в середине пирамиды”
- RAW: запрещён
- содержит DEFAULT_PIPE_ID (KEY) и REQUIRED_IDX_LOCAL (KEY)

Это НЕ обязаловка для каждой папки. Только для доменных хабов.

---

## [M] NAMING RULE (STRICT)
Имя обязано содержать имя папки, за которую отвечает файл.

Формат:
- 00__<FOLDER>__INDEX_MANIFEST.md
- 00__<FOLDER>__PIPELINE_CONTRACT.md
- 00__<FOLDER>__START_NODE.md (если нужен)

Где <FOLDER> — точное имя папки как в дереве.

---

## [M] READMEs / REALMEs / RELEASEs POLICY
- README: не используется как системный файл (только для людей, если когда-нибудь понадобится)
- REALM/LAWS: живут в UE_V2/01_LAW или UE_V2/00_BOOT (системные), но НЕ как “папочные README”
- RELEASE NOTES: только в UE_V2/12_LOG или отдельном релиз-разделе, не в каждой папке

---

## [M] OUTPUT CANON
Система для входа в папку всегда делает:
1) открыть INDEX_MANIFEST
2) затем открыть PIPELINE_CONTRACT
3) затем открыть 1–3 целевых файла (минимум)

---

## [M] GATES
PASS если:
- INDEX_MANIFEST и PIPELINE_CONTRACT существуют
- KEY резолвятся, RAW только в INDEX_MANIFEST
GAP если:
- отсутствует любой из двух обязательных файлов
- PIPELINE_CONTRACT содержит RAW
