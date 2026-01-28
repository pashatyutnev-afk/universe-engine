# 14__PIPE_REL

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: PIPE
UID: UE.V2.PIPE.REL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Релизный пайп: упаковка, readiness, drop rules, пост-релиз контроль.

---

## [M] INTENT
Сделать релизы частью системы (не "сбоку"): обязательные стадии, проверки, упаковка и логи.

---

## [M] INPUTS
- ROUTE_TOKEN (DOMAIN=REL или ARTIFACT_TYPE=RELEASE_PACK)
- BRIEF_TOKEN / PLAN_TOKEN
- контент-артефакт (трек/альбом/пак), если релиз привязан к контенту

---

## [M] OUTPUTS
- PACK_TOKEN (релизный пакет)
- REPORT_TOKEN (VAL/QA)
- BASELINE_TOKEN (signoff)

---

## [M] STAGES (REL)
S0 INTAKE:
- подтвердить что релизим (что именно, куда, какие версии)

S2 PLAN:
- определить coverage level (release_ready/masterpiece)
- выбрать обязательные проверки по XREF validation matrix

S3 KB:
- подтянуть релизные правила: naming, credits, drop rules

S5 PRODUCTION:
- собрать RELEASE_PACK (метаданные, версии, описания, обложка если применимо, экспорт)

S6 REVIEW:
- CTL: полнота/лимиты/соответствие
- VAL: pack ready, naming collision, credits/rights
- QA: regression guard, differentiation (если релиз серийный)

S7 FIX:
- правки по отчётам

S8 PACK:
- финальная упаковка (структура папок/файлов, чеклист)

S9 SIGNOFF:
- SPC подтверждает baseline

S10 POST:
- запись в CHANGE_LOG/DECISION_LOG
- обновление каталога/индексов при необходимости

---

## [M] REQUIRED_CHECKS (DEFAULT)
- CTL: readiness + noise
- VAL: release_pack_ready + naming_collision + credits_rights
- QA: regression_guard + differentiation (если применимо)

---

## [M] GATES
PASS если:
- есть PACK_TOKEN + REPORT_TOKEN(QA/VAL) + BASELINE_TOKEN
REWORK если:
- нет метаданных/версий/экспорта
GAP если:
- отсутствует обязательный валидатор/QA или IDX_REL
STOP если:
- нарушены законы доступа/manifest/entrypoint
