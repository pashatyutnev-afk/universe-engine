# RESEARCH & FACT CHECKING (KB REALM)
FILE: 04_KNOWLEDGE_BASE/08__RESEARCH_FACT_CHECKING.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_REALM
REALM: RESEARCH
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.REALM.RESEARCH.001
OWNER: SYSTEM
ROLE: Canonical knowledge realm for research, source validation, and fact-checking discipline: claims, evidence, confidence, citation hygiene, and canon-safe updates

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Realm Research & Fact Checking канонизирован: дисциплина утверждений, уровни уверенности, правила источников и фиксации"
- REASON: "Без исследовательской дисциплины канон засоряется догадками и противоречиями"
- IMPACT: "Все проекты: факты, мирострой, исторические элементы, научные элементы"

---

## 0) PURPOSE
Этот realm — база знаний “как проверять и фиксировать факты”.

Он задаёт:
- как формулировать утверждения (claims)
- как привязывать доказательства (evidence)
- как маркировать уверенность (confidence)
- как обновлять факты без разрушения канона

---

## 1) BOUNDARIES (HARD)
### 1.1 This realm IS
- дисциплина утверждений и источников
- правила интерпретации и допущений
- правила фиксации обновлений (без скрытых замен)

### 1.2 This realm IS NOT
- системные законы канона/версий (это system law)
- художественные решения “как лучше” (это realms по смыслу)

---

## 2) CLAIM MODEL (MANDATORY)
Любая “фактическая” строка должна быть одного из типов:

1) **OBSERVED** — наблюдение (что видно/замерено)
2) **REPORTED** — сообщено источником
3) **INFERRED** — вывод из наблюдений/источников
4) **SPECULATIVE** — гипотеза/предположение

Правило:
- нельзя подавать INFERRED/SPECULATIVE как OBSERVED/REPORTED.

---

## 3) CONFIDENCE SCALE (STANDARD)
- **C0** — не проверено (идея)
- **C1** — слабое подтверждение (1 источник или косвенно)
- **C2** — среднее (2+ независимых источника или сильная первичка)
- **C3** — высокое (первичные данные + независимая верификация)

Рекомендуемо:
- канон-факты мира держать минимум на **C2**.

---

## 4) SOURCE HYGIENE (RULES)
### 4.1 Prefer primary sources
Приоритет:
1) первичные документы/данные/исследования
2) официальные публикации/институты
3) уважаемые вторичные обзоры
4) мнения/блоги — только как указатели, не как SoT

### 4.2 Independence rule
“2 источника” имеют смысл только если они независимы (не перепечатка).

### 4.3 Quote discipline
Если нужен текст — цитируем коротко и по делу.
Остальное — пересказ с пометкой типа claim.

---

## 5) UPDATE DISCIPLINE (CANON-SAFE)
Когда факт обновился:
- не переписываем тихо
- добавляем запись изменения (что было → что стало → почему)
- сохраняем предыдущую версию смысла как “historical note”, если это важно для канона

---

## 6) RED FLAGS (COMMON FAILURES)
- “все знают что…” без источника
- “это точно” при C0/C1
- один источник, который сам на кого-то ссылается
- смешивание художественного решения с фактом без маркировки

---

## 7) CHECKLISTS (KB)
### 7.1 Fact check pass/fail
- [ ] утверждение классифицировано (Observed/Reported/Inferred/Speculative)
- [ ] указан источник (если Reported)
- [ ] указана уверенность C0–C3
- [ ] нет подмены гипотезы под факт
- [ ] есть независимость (если 2+ источника)

### 7.2 Canon-safe update
- [ ] есть “что изменилось”
- [ ] есть “почему изменилось”
- [ ] есть “что это ломает” (если ломает)
- [ ] обновление прошло change management (если это SoT)

---

## 8) OUTPUT POINTERS
Этот realm обычно “производит”:
- research notes (claims + evidence + confidence)
- список источников по теме
- карты противоречий (что не бьётся)

---

## 9) XREF (MANDATORY POINTERS)
XREF_DOC: 04_KNOWLEDGE_BASE/07__REFERENCE_GLOSSARY.md | WHY:термины “claim/evidence/confidence” должны быть едины
XREF_DOC: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md | WHY:правила управления KB должны определять, что считается каноном

---

## 10) NEXT EXTENSIONS (CONTROLLED)
Если понадобится:
- шаблон “Research Note” как KB entity passport
- реестр источников (как system file в KB governance или standards)

--- END.
