# 04__REG_ENTITY_CATALOG

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: REGISTRY
UID: UE.V2.REG.ENT.CATALOG.001
VERSION: 1.2.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Единый каталог всех сущностей: совместимость, роль, стадия, IO, KB scope, путь. Основа автоматического выбора участников (без блуждания).

---

## [M] INTENT
Сделать выбор участников детерминированным и масштабируемым на сотни сущностей:
ORC/CTL/VAL/QA выбираются и проверяются через этот каталог + XREF карты + KB_SCOPE.

---

## [M] RULES
1) Любая сущность, участвующая в цепочке, обязана иметь запись в этом каталоге.
2) PATH не является идентификатором. Идентификатор: UID.
3) Любое переименование/переезд меняет только PATH_REF и фиксируется в CHANGE_LOG.
4) ROLE/CAP/STAGE/IO обязаны соответствовать словарям:
   - CAP: UE_V2/03_ENT/00_REG/05__REG_CAPABILITIES.md
   - STAGE: UE_V2/02_STD/18__PIPELINE_STAGE_MODEL.md
   - IO: UE_V2/02_STD/19__IO_TYPES.md
5) Если сущности/записи нет — GAP (создать запись).
6) Если KB_SCOPE_ID отсутствует и это не bootstrap-ядро — GAP.
7) В одном STEP активные сущности ограничены NOISE_BUDGET + STEP_BUDGET_CTL (для доменов).

---

## [M] TABLE_SCHEMA
Колонки (в порядке):
- UID
- ENTITY_NAME
- ROLE                (SPC|ORC|ENG|CTL|VAL|QA|XREF|REG|TPL|DOMAIN_PLUGIN)
- DOMAIN              (CORE|MUSIC|VIS|LOR|REL|...)
- CAP                 (csv)
- STAGE               (csv: S0_INTAKE..S10_POST)
- IO_IN               (csv IO types)
- IO_OUT              (csv IO types)
- REQUIRES            (csv UID или ROLE@DOMAIN)
- INCOMPATIBLE        (csv UID или INC.* tags)
- KB_SCOPE_ID         (KB.SCOPE.*)
- STATUS              (ACTIVE|DRAFT|DEPRECATED)
- PRIORITY            (CORE|HIGH|MED|LOW)
- PATH_REF            (path to file)
- NOTES               (1 строка)

---

## [M] TABLE (APPEND ONLY)
| UID | ENTITY_NAME | ROLE | DOMAIN | CAP | STAGE | IO_IN | IO_OUT | REQUIRES | INCOMPATIBLE | KB_SCOPE_ID | STATUS | PRIORITY | PATH_REF | NOTES |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|

### CORE (known anchors)
| UE.V2.CTL.READINESS.001 | CTL_READINESS | CTL | CORE | cap.control,cap.gate | S2_PLAN,S6_REVIEW | IO.PLAN,IO.TRACE | IO.REPORT.CTL | - | - | KB.SCOPE.CORE.GOV | ACTIVE | CORE | UE_V2/06_PIPE/06__CTL_READINESS.md | System readiness control |
| UE.V2.CTL.NOISE.001 | CTL_NOISE_BUDGET | CTL | CORE | cap.control,cap.noise | S2_PLAN,S6_REVIEW | IO.PLAN,IO.TRACE | IO.REPORT.CTL | - | - | KB.SCOPE.CORE.GOV | ACTIVE | CORE | UE_V2/06_PIPE/07__CTL_NOISE.md | Context/noise budget control |
| UE.V2.VAL.DOC.001 | VAL_DOC_FMT | VAL | CORE | cap.validate,cap.docfmt | S6_REVIEW | IO.PLAN,IO.TRACE | IO.REPORT.VAL | - | - | KB.SCOPE.CORE.STD | ACTIVE | CORE | UE_V2/06_PIPE/08__VAL_DOC.md | Doc format/markers validation |
| UE.V2.QA.ACCEPT.001 | QA_ACCEPT | QA | CORE | cap.qa,cap.accept | S6_REVIEW | IO.REPORT.VAL,IO.REPORT.CTL | IO.REPORT.QA | - | - | KB.SCOPE.CORE.QA | ACTIVE | CORE | UE_V2/06_PIPE/11__QA_ACCEPT.md | Accept/reject gate |
| UE.V2.XREF.VALMATRIX.001 | MAP__VALIDATION_MATRIX | XREF | CORE | cap.map,cap.validate | S2_PLAN,S6_REVIEW | IO.PLAN | IO.PLAN | - | - | KB.SCOPE.CORE.GOV | ACTIVE | CORE | UE_V2/03_ENT/08_XREF/03__MAP__VALIDATION_MATRIX.md | Validation requirements map |
| UE.V2.XREF.PIPELINES.001 | MAP__PIPELINES | XREF | CORE | cap.map,cap.route | S1_ROUTE,S2_PLAN | IO.ROUTE | IO.PLAN | - | - | KB.SCOPE.CORE.GOV | ACTIVE | CORE | UE_V2/03_ENT/08_XREF/04__MAP__PIPELINES.md | Pipeline routing map |

### MUSIC (core runtime set)
| UE.V2.ORC.MUSIC.TRACK_BUILD_STEP.001 | TRACK_BUILD_STEP_ORC | ORC | MUSIC | cap.route,cap.orchestrate,cap.plan | S0_INTAKE,S2_PLAN,S4_OPTIONS,S5_PRODUCTION,S6_REVIEW,S7_FIX,S8_PACK,S9_SIGNOFF | IO.BRIEF,IO.ROUTE,IO.PLAN,IO.KB_SCOPE | IO.PLAN,IO.OPTIONS,IO.DECISION,IO.DELTA,IO.PACK,IO.BASELINE | CTL@MUSIC,QA@MUSIC,VAL@MUSIC | - | KB.SCOPE.MUSIC.PROD | ACTIVE | HIGH | UE_V2/03_ENT/03_ORC/10_MUSIC_ORCHESTRATORS/07__TRACK_BUILD_STEP_ORC.md | Default ORC for MUSIC.TRACK |
| UE.V2.ORC.MUSIC.HOOK_FOCUS_LOOP.001 | HOOK_FOCUS_LOOP_ORC | ORC | MUSIC | cap.orchestrate,cap.hook,cap.score | S4_OPTIONS,S7_FIX | IO.MUSIC.HOOK_OPTIONS,IO.DECISION | IO.MUSIC.HOOK_OPTIONS,IO.DECISION,IO.DELTA,IO.REPORT.QA | CTL@MUSIC,QA@MUSIC | - | KB.SCOPE.MUSIC.PROD | ACTIVE | HIGH | UE_V2/03_ENT/03_ORC/10_MUSIC_ORCHESTRATORS/08__HOOK_FOCUS_LOOP_ORC.md | Focus-loop hook improvement |
| UE.V2.ORC.MUSIC.MIX_FOCUS_LOOP.001 | MIX_FOCUS_LOOP_ORC | ORC | MUSIC | cap.orchestrate,cap.mix,cap.score | S5_PRODUCTION,S7_FIX | IO.MUSIC.MIX_PLAN,IO.REPORT.QA | IO.MUSIC.MIX_PLAN,IO.DELTA,IO.REPORT.QA | CTL@MUSIC,QA@MUSIC | - | KB.SCOPE.MUSIC.PROD | ACTIVE | HIGH | UE_V2/03_ENT/03_ORC/10_MUSIC_ORCHESTRATORS/09__MIX_FOCUS_LOOP_ORC.md | Focus-loop mix translation polish |
| UE.V2.ORC.MUSIC.LYRICS_FOCUS_LOOP.001 | LYRICS_FOCUS_LOOP_ORC | ORC | MUSIC | cap.orchestrate,cap.lyrics,cap.score | S4_OPTIONS,S5_PRODUCTION,S7_FIX | IO.BRIEF,IO.OPTIONS,IO.DECISION | IO.DELTA,IO.PACK,IO.REPORT.QA | CTL@MUSIC,QA@MUSIC | - | KB.SCOPE.MUSIC.LYRICS | ACTIVE | MED | UE_V2/03_ENT/03_ORC/10_MUSIC_ORCHESTRATORS/10__LYRICS_FOCUS_LOOP_ORC.md | Focus-loop lyrics/hook line |
| UE.V2.ORC.MUSIC.IDENTITY_BUILD.001 | IDENTITY_BUILD_ORC | ORC | MUSIC | cap.plan,cap.orchestrate,cap.pack | S0_INTAKE,S2_PLAN,S3_KB,S4_OPTIONS,S5_PRODUCTION,S6_REVIEW,S8_PACK,S9_SIGNOFF | IO.BRIEF,IO.ROUTE | IO.PACK,IO.BASELINE | CTL@MUSIC,QA@MUSIC,VAL@MUSIC | - | KB.SCOPE.MUSIC.PROD | ACTIVE | MED | UE_V2/03_ENT/03_ORC/10_MUSIC_ORCHESTRATORS/11__IDENTITY_BUILD_ORC.md | Artist/group DNA pack |
| UE.V2.ORC.MUSIC.MERGE_SYNTHESIS.001 | MERGE_SYNTHESIS_ORC | ORC | MUSIC | cap.orchestrate,cap.score,cap.transform,cap.differentiate | S5_PRODUCTION,S6_REVIEW,S7_FIX | IO.OPTIONS,IO.MUSIC.SELECTION,IO.REPORT.QA,IO.REPORT.VAL,IO.REPORT.CTL | IO.DELTA,IO.REPORT.QA,IO.REPORT.VAL | CTL@MUSIC,VAL@MUSIC,QA@MUSIC | - | KB.SCOPE.MUSIC.PROD | ACTIVE | HIGH | UE_V2/03_ENT/03_ORC/10_MUSIC_ORCHESTRATORS/12__MERGE_SYNTHESIS_ORC.md | Best-of synthesis from attempts |
| UE.V2.CTL.MUSIC.STEP_BUDGET.001 | STEP_BUDGET_CTL | CTL | MUSIC | cap.control,cap.noise,cap.gate | S2_PLAN,S4_OPTIONS,S5_PRODUCTION,S6_REVIEW | IO.PLAN,IO.TRACE | IO.REPORT.CTL | ORC@MUSIC | - | KB.SCOPE.MUSIC.PROD | ACTIVE | HIGH | UE_V2/03_ENT/05_CTL/10_MUSIC_CONTROLLERS/14__STEP_BUDGET_CTL.md | Limits per step/options/passes |
| UE.V2.CTL.MUSIC.VARIANT_POLICY.001 | VARIANT_POLICY_CTL | CTL | MUSIC | cap.control,cap.plan | S4_OPTIONS | IO.BRIEF,IO.PLAN | IO.OPTIONS | ORC@MUSIC | - | KB.SCOPE.MUSIC.PROD | ACTIVE | HIGH | UE_V2/03_ENT/05_CTL/10_MUSIC_CONTROLLERS/15__VARIANT_POLICY_CTL.md | Make variants meaningfully different |
| UE.V2.CTL.MUSIC.FOCUS_LOOP_STOP.001 | FOCUS_LOOP_STOP_RULES_CTL | CTL | MUSIC | cap.control,cap.gate | S7_FIX,S6_REVIEW | IO.REPORT.QA,IO.REPORT.VAL,IO.DELTA | IO.REPORT.CTL | ORC@MUSIC | - | KB.SCOPE.MUSIC.PROD | ACTIVE | HIGH | UE_V2/03_ENT/05_CTL/10_MUSIC_CONTROLLERS/16__FOCUS_LOOP_STOP_RULES_CTL.md | Stop/continue rules for loops |
| UE.V2.CTL.MUSIC.SYNTHESIS_MERGE_POLICY.001 | SYNTHESIS_MERGE_POLICY_CTL | CTL | MUSIC | cap.control,cap.gate,cap.coverage | S5_PRODUCTION,S6_REVIEW | IO.OPTIONS,IO.REPORT.QA,IO.REPORT.VAL | IO.REPORT.CTL | ORC@MUSIC | - | KB.SCOPE.MUSIC.PROD | ACTIVE | HIGH | UE_V2/03_ENT/05_CTL/10_MUSIC_CONTROLLERS/17__SYNTHESIS_MERGE_POLICY_CTL.md | Limit component mixing, avoid monsters |
| UE.V2.VAL.MUSIC.CHAIN_COMPLETENESS.001 | CHAIN_COMPLETENESS_VAL | VAL | MUSIC | cap.validate,cap.trace | S6_REVIEW,S8_PACK | IO.PLAN,IO.TRACE,IO.REPORT.CTL | IO.REPORT.VAL | ORC@MUSIC,CTL@MUSIC | - | KB.SCOPE.MUSIC.PROD | ACTIVE | HIGH | UE_V2/03_ENT/06_VAL/10_MUSIC_VALIDATORS/11__CHAIN_COMPLETENESS_VAL.md | Tokens/decisions/archive completeness |
| UE.V2.VAL.MUSIC.COVERAGE_PASS.001 | COVERAGE_PASS_VAL | VAL | MUSIC | cap.validate,cap.coverage | S6_REVIEW,S9_SIGNOFF | IO.PLAN,IO.TRACE | IO.REPORT.VAL | CTL@MUSIC | - | KB.SCOPE.MUSIC.PROD | ACTIVE | HIGH | UE_V2/03_ENT/06_VAL/10_MUSIC_VALIDATORS/12__COVERAGE_PASS_VAL.md | Pillars coverage validation |
| UE.V2.VAL.MUSIC.PROMPT_SPEC.001 | PROMPT_SPEC_VAL | VAL | MUSIC | cap.validate,cap.docfmt | S6_REVIEW | IO.MUSIC.PROMPT_SPEC,IO.KB_SCOPE | IO.REPORT.VAL | ORC@MUSIC,CTL@MUSIC | - | KB.SCOPE.MUSIC.PROD | ACTIVE | MED | UE_V2/03_ENT/06_VAL/10_MUSIC_VALIDATORS/13__PROMPT_SPEC_VAL.md | Prompt spec contract compliance |
| UE.V2.VAL.MUSIC.SYNTHESIS_COHERENCE.001 | SYNTHESIS_COHERENCE_VAL | VAL | MUSIC | cap.validate,cap.differentiate | S6_REVIEW | IO.DELTA,IO.REPORT.QA | IO.REPORT.VAL | ORC@MUSIC,CTL@MUSIC | - | KB.SCOPE.MUSIC.PROD | ACTIVE | HIGH | UE_V2/03_ENT/06_VAL/10_MUSIC_VALIDATORS/14__SYNTHESIS_COHERENCE_VAL.md | Composite coherence after merge |
| UE.V2.QA.MUSIC.TRACK_PANEL.001 | TRACK_QA_PANEL_QA | QA | MUSIC | cap.qa,cap.accept,cap.score | S6_REVIEW | IO.MUSIC.SELECTION,IO.KB_SCOPE | IO.MUSIC.TRACK_QA_REPORT,IO.REPORT.QA | - | - | KB.SCOPE.MUSIC.PROD | ACTIVE | HIGH | UE_V2/03_ENT/07_QA/10_MUSIC_QA/10__TRACK_QA_PANEL_QA.md | Aggregates QA 01–09 into one report |

---

## [M] APPEND_ONLY_POLICY
- Каталог расширяется добавлением строк.
- Изменения существующих строк фиксируются в UE_V2/12_LOG/02__CHANGE_LOG.md.

---

## [M] GATES
PASS если:
- для участника цепочки найдена строка по UID
- ROLE/CAP/STAGE/IO валидны
GAP если:
- отсутствует запись или KB_SCOPE_ID
REWORK если:
- PATH используется как идентификатор
STOP если:
- каталог недоступен по RAW при выполнении (для режимов, где он обязателен)
