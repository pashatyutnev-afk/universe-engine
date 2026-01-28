# 17__SYNTHESIS_MERGE_POLICY_CTL

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: CTL
UID: UE.V2.CTL.MUSIC.SYNTHESIS_MERGE_POLICY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Политика синтеза: как выбирать победителей, сколько брать компонентов, как не собрать монстра.

---

## [M] INTENT
Сделать синтез управляемым: брать лучшее, не ломая целостность и не перегружая итерациями.

---

## [M] RULES
1) Синтез выполняется только если есть:
   OPTIONS/SELECTION + QA/VAL/CTL reports.
2) В одном синтезе переносим максимум:
   - HOOK: 2 компонента
   - ARRANGEMENT: 2 компонента
   - PALETTE: 2 компонента
   - MIX/MASTER: 2 компонента
   Итого не более 8 переносов за один SYNTHESIS_TOKEN.
3) Запрещены "несовместимые" переносы:
   - если QA/VAL пометили конфликт (masking/loop/recognition), перенос не делается без отдельного FIX pass.
4) Обязателен SCORE_TOKEN перед SYNTHESIS_TOKEN (кроме FAST режима).
5) После синтеза обязателен QA panel прогон.

---

## [M] OUTPUTS
- REPORT_TOKEN(CTL): PASS/REWORK + что сократить/что нельзя смешивать

---

## [M] GATES
PASS если:
- соблюдены лимиты переносов и есть SCORE_TOKEN
REWORK если:
- попытка смешать слишком много компонентов или игнор fail flags
