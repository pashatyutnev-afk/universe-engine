# 07__MAP__COVERAGE_TO_ENTITIES

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: XREF / MAP
UID: UE.V2.XREF.COVERAGE_TO_ENTITIES.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Карта "Pillars -> типы сущностей/капабилити", чтобы ORC мог набрать участников для покрытия.

---

## [M] INTENT
Сделать "шедевр со всех сторон" автоматизируемым: ORC закрывает Pillars через эту карту, не вызывая всех подряд.

---

## [M] RULES
1) Источник Pillars: STD/16__COVERAGE_RULES.md.
2) ORC выбирает минимально достаточных участников, чтобы закрыть требуемые Pillars.
3) Если Pillar не может быть закрыт (нет сущностей), это GAP (создать сущность или разрешить исключение).

---

## [M] MAP (DEFAULT)
P0 GOAL_FIT:
- prefer: SPC(cap.plan), ORC(cap.plan)
- supporting: CTL(cap.control)

P1 CORE_CRAFT:
- prefer: ENG(cap.generate/cap.structure/cap.hook/cap.palette), SPC(cap.review)
- supporting: ORC(cap.orchestrate)

P2 EMOTION_PSYCH:
- prefer: SPC(psychology), ENG(cap.hook) where applicable
- supporting: QA(score)

P3 UNIQUENESS:
- prefer: QA(cap.differentiate), VAL(cap.validate collision), ENG(trend/genre)
- supporting: CTL(threshold policies)

P4 TECH_QUALITY:
- prefer: QA(loop/mix translation), VAL(repeat/prompt fidelity), ENG(mix/master)
- supporting: CTL(quality gates)

P5 PACKAGING:
- prefer: ORC(cap.pack), CTL(metadata policy), VAL(pack ready)
- supporting: SPC(signoff)

P6 COMPLIANCE:
- prefer: CTL(compliance), VAL(credits/rights/canon), XREF(rule hierarchy)
- supporting: QA(accept)

P7 DELIVERY:
- prefer: ORC(release_pack), SPC(marketing/distribution), CTL(drop rules)
- supporting: QA(regression guard)

---

## [M] GATES
PASS если:
- для каждого обязательного Pillar выбран хотя бы один участник (по карте)
REWORK если:
- участники не связаны с Pillar (случайный выбор)
GAP если:
- Pillar обязателен, но нет доступных сущностей
