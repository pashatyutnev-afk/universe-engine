# 05__MAP__ENTITY_IO_TYPES

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: XREF / MAP
UID: UE.V2.XREF.ENTITY_IO_TYPES.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Карта IO типов: какие входы/выходы считаются совместимыми и как стыкуются шаги.

---

## [M] INTENT
Свести совместимость к правилам стыковки IO (вместо "по памяти"), чтобы ORC мог автоматически собрать цепочку.

---

## [M] RULES
1) Источник истины по именам IO типов: STD/19__IO_TYPES.md.
2) Любой STEP обязан объявлять IO_IN и IO_OUT.
3) Стыковка считается валидной, если IO_OUT(prev) ∩ IO_IN(next) ≠ ∅.
4) Если IO тип отсутствует в STD — GAP (добавить IO_TYPE).
5) Если стыковки нет — REWORK (менять шаг или вставлять трансформер).

---

## [M] COMPATIBILITY_MAP (HIGH LEVEL)
CORE FLOW:
- IO.BRIEF -> IO.ROUTE, IO.PLAN
- IO.ROUTE -> IO.PLAN
- IO.PLAN -> IO.KB_SCOPE, IO.OPTIONS, IO.TRACE
- IO.KB_SCOPE -> IO.OPTIONS, IO.PROMPT_SPEC, IO.PROD_DRAFT
- IO.OPTIONS -> IO.DECISION
- IO.DECISION -> IO.DELTA, IO.PROD_DRAFT
- IO.REPORT.CTL + IO.REPORT.VAL -> IO.REPORT.QA
- IO.REPORT.QA -> IO.DELTA, IO.PACK
- IO.PACK -> IO.BASELINE

MUSIC FLOW:
- IO.MUSIC.HOOK_OPTIONS -> IO.DECISION
- IO.MUSIC.STRUCTURE_MAP -> IO.MUSIC.PROMPT_SPEC, IO.MUSIC.GEN_PLAN
- IO.MUSIC.PALETTE_SPEC -> IO.MUSIC.PROMPT_SPEC
- IO.MUSIC.PROMPT_SPEC -> IO.MUSIC.GEN_PLAN
- IO.MUSIC.GEN_PLAN -> IO.MUSIC.SELECTION
- IO.MUSIC.SELECTION -> IO.MUSIC.MIX_PLAN
- IO.MUSIC.MIX_PLAN -> IO.MUSIC.MASTER_PLAN
- IO.MUSIC.MASTER_PLAN -> IO.MUSIC.TRACK_QA_REPORT
- IO.MUSIC.TRACK_QA_REPORT -> IO.MUSIC.RELEASE_PACK, IO.PACK

---

## [M] TRANSFORMER_POLICY
Если нужен мост между IO типами:
- вставить сущность CAP=cap.transform с IO_IN=A и IO_OUT=B
- или включить FOCUS-LOOP для доработки входа до совместимого выхода

---

## [M] GATES
PASS если:
- шаги пайпа стыкуются по IO правилам
REWORK если:
- есть разрывы IO
GAP если:
- нужен новый IO_TYPE или трансформер-сущность
