# CROSSREF REALM — README (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__README__CROSSREF.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: README (REALM)
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.REALM.README.001
OWNER: SYSTEM
ROLE: Explains what CROSSREF is, what lives here, and how maps are authored/maintained.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Created deterministic README for XREF realm: purpose, boundaries, artifacts, authoring rules."
- REASON: "Make routing visible and auditable; reduce guesswork."
- IMPACT: "XREF becomes stable SoT for stitching maps and pipeline discoverability."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.README.001

---

## 0) PURPOSE (LAW)
`90_XREF__CROSSREF` — слой “стыковки”.
Здесь лежат карты соответствий между сущностями и слоями: ENG↔ORC↔SPC, пайплайны, матрицы валидации, правила XREF.

---

## 1) WHAT LIVES HERE (SCOPE)
- Realm index: `00__INDEX__CROSSREF.md`
- Rules: `01__RULES__XREF.md`
- Maps:
  - ENG → ORC: `01__MAP__ENG_TO_ORC.md`
  - ORC → SPC: `02__MAP__ORC_TO_SPC.md`
  - Validation matrix: `03__MAP__VALIDATION_MATRIX.md`
  - Pipelines: `04__MAP__PIPELINES.md`
- Authoring flow: `02__CREATE_FLOW__XREF.md`
- Templates:
  - XREF index template
  - XREF record template

---

## 2) BOUNDARIES (HARD)
IN SCOPE:
- Только карты/правила/матрицы/переходы.
OUT OF SCOPE:
- Сами сущности (SPC/ORC/ENG/CTL/VAL/QA) — они живут в своих реестрах.
- Изменение стандартов — это 02_STANDARDS и STANDARDS OWNER.

---

## 3) PRIMARY LAW
- XREF не “описание в чате”. XREF — это документы-артефакты.
- XREF должен быть:
  - детерминированным (одна интерпретация),
  - проверяемым (табличная/схемная форма),
  - пригодным для маршрутизации (routing-ready).

---

## 4) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- примеры карт и схем маршрутизации
KB OUTPUTS:
- нет, если отдельно не поставлена задача “KB module”

---

## 5) INTERFACES (RAW ONLY)
- Runtime entrypoint:
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/01__START_UNIVERSE_ENGINE.md

--- END.
