# SPC FAMILY REALM — RESEARCH SPECIALISTS (CANON)
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/09_RESEARCH/00__README_RESEARCH_SPECIALISTS.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
DOC_TYPE: README
INDEX_TYPE: FAMILY_REALM
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.REALM.RESEARCH.001
OWNER: SYSTEM
ROLE: Family realm definition + boundaries + navigation rules for SPC family `09_RESEARCH`

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established RESEARCH SPC family realm: research direction, scientific/historical/cultural research, knowledge curation, source validation, fact checking, and speculative plausibility gates."
- REASON: "Need deterministic evidence and plausibility pipeline to prevent canon drift, misinformation, and unsupported claims."
- IMPACT: "System becomes audit-friendly: claims are traceable, risks are classified, and speculative content is clearly gated."
- CHANGE_ID: UE.CHG.2026-01-09.SPC.REALM.RESEARCH.001

---

## 0) PURPOSE (LAW)
Семейство `09_RESEARCH` отвечает за доказуемость и правдоподобие:
- где мы берём знания и как их проверяем
- какие утверждения допустимы как факты
- какие утверждения допустимы как гипотезы/спекуляции
- как предотвращаем “фейк-канон” и дрейф терминов
- как оформляем проверки (records) и гейты PASS/FAIL

Цель семьи — чтобы “знание” в системе было управляемым: проверяемым, трассируемым и безопасным.

---

## 1) EXISTENCE + NAV RULE (MANDATORY)
- Специалист существует для системы **только если**:
  1) зарегистрирован в глобальном SPC INDEX:
     `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md`
  2) и файл лежит по каноническому пути
- Любые файлы в папке без регистрации — **NON-CANON / ignored**
- Каноническая навигация по семье — через RAW ссылки глобального SPC INDEX

---

## 2) FAMILY SCOPE
**FAMILY NAME:** RESEARCH SPECIALISTS  
**FAMILY PATH:** `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/09_RESEARCH/`

### 2.1 Covered domains (what we DO)
- Research direction & research plans
- Scientific research (physics/biology/etc. as needed)
- Historical research (epochs/events/chronology)
- Cultural anthropology (culture/rituals/values/language risks)
- Knowledge curation (KB shaping and claim hygiene)
- Source validation (source credibility & provenance)
- Fact checking (claim-level verification)
- Speculative plausibility (what is “could work” and under what assumptions)

### 2.2 Hard boundaries (what we DO NOT do)
- Мы не “придумываем факты” и не выдаём мнение как доказанность.
- Мы не переписываем канон — мы классифицируем утверждения и даём гейты.
- Мы не делаем политические/медицинские/опасные утверждения как факты без отдельной проверки.
- Мы не заменяем творческие решения — мы маркируем риски и условия правдоподобия.

---

## 3) CLAIM CLASS STANDARD (MANDATORY)
Каждое утверждение в системе должно быть классифицировано одним из типов:
- **FACT:** проверено (есть подтверждение/источник)
- **INFERENCE:** вывод из фактов (логика указана)
- **HYPOTHESIS:** гипотеза (требует проверки)
- **SPECULATION:** художественная спекуляция (допустима при явной маркировке)
- **UNVERIFIED:** не проверено (запрещено для канона как факт)

---

## 4) PRIORITY STANDARD (S0–S3) (MANDATORY)
При проверках используем единый приоритет (блокирующие/неблокирующие):
- **PRIORITY: S0** — блокер: ломает канон/безопасность/доказуемость
- **PRIORITY: S1** — сильный риск: высокий шанс ошибки/скандала/дрейфа
- **PRIORITY: S2** — средний риск: требуется уточнение/маркировка
- **PRIORITY: S3** — мелочь/стилистика/низкий риск

---

## 5) KNOWLEDGE BASE (KB) SCOPE (MANDATORY)
### 5.1 KB INPUTS
- Research & Fact Checking realm  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/08__RESEARCH_FACT_CHECKING.md
- Reference Glossary realm  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/07__REFERENCE_GLOSSARY.md
- Production Pipeline realm (как оформлять records/пакеты)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/05__PRODUCTION_PIPELINE.md

### 5.2 KB OUTPUTS
- Единые шаблоны: claim records, evidence notes, validation reports.
- Нормализация терминов и “запрет фейк-терминов”.

### 5.3 KB BOUNDARIES
- Любая научная/историческая “достоверность” должна быть оформлена как FACT/INFERENCE/HYPOTHESIS, не как “всем известно”.

---

## 6) INTERFACES (SYSTEM LINKS) — RAW ONLY
### 6.1 ENG (Engines) — typical support
- Scientific plausibility validator engine  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/11_VALIDATION_ENGINES/06__SCIENTIFIC_PLAUSIBILITY_ENG.md
- Historical accuracy validator engine  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/11_VALIDATION_ENGINES/05__HISTORICAL_ACCURACY_ENG.md
- Cultural accuracy validator engine  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/11_VALIDATION_ENGINES/04__CULTURAL_ACCURACY_ENG.md

### 6.2 ORC — typical usage
ORC вызывает RESEARCH SPC когда нужно:
- поставить план исследований (Research Director)
- проверить научные/исторические/культурные утверждения
- собрать и нормализовать термины и знания (Knowledge Curator)
- верифицировать источники (Source Validation)
- проверить утверждения поштучно (Fact Checking)
- оценить правдоподобие спекуляции (Speculative Plausibility)

---

## 7) FAMILY NAV — SPECIALISTS (ORDER IS LAW)
01 — RESEARCH DIRECTOR  
02 — SCIENTIFIC RESEARCHER  
03 — HISTORICAL RESEARCHER  
04 — CULTURAL ANTHROPOLOGIST  
05 — KNOWLEDGE CURATOR  
06 — SOURCE VALIDATION SPECIALIST  
07 — FACT CHECKING SPECIALIST  
08 — SPECULATIVE PLAUSIBILITY ANALYST  

---

## FINAL RULE (LOCK)
Этот README задаёт границы семьи `09_RESEARCH`.  
Если утверждение не классифицировано (FACT/INFERENCE/HYPOTHESIS/SPECULATION/UNVERIFIED) — оно не может считаться надёжной опорой канона.

--- END.
