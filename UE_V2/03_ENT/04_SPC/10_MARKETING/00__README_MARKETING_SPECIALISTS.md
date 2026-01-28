# SPC FAMILY REALM — MARKETING SPECIALISTS (CANON)
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/10_MARKETING/00__README_MARKETING_SPECIALISTS.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
DOC_TYPE: README
INDEX_TYPE: FAMILY_REALM
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.REALM.MARKETING.001
OWNER: SYSTEM
ROLE: Family realm definition + boundaries + navigation rules for SPC family `10_MARKETING`

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established MARKETING SPC family realm: brand architecture, audience analysis/research, content packaging, platform distribution, SEO discovery, trailers/teasers, community, engagement, growth, and monetization strategy as a deterministic system."
- REASON: "Need structured discovery and distribution pipeline so releases reach audiences consistently without canon drift or manipulative promises."
- IMPACT: "Marketing becomes audit-friendly: clear roles, measurable outputs, and controlled messaging aligned with canon and production."
- CHANGE_ID: UE.CHG.2026-01-09.SPC.REALM.MARKETING.001

---

## 0) PURPOSE (LAW)
Семейство `10_MARKETING` отвечает за обнаружение, упаковку и распространение продукта:
- бренд и позиционирование
- аудитория: анализ и исследование
- упаковка контента (сообщения/структуры/пакеты)
- распределение по платформам и каналы
- SEO и органическое обнаружение
- трейлеры/тизеры (как упаковка обещаний)
- комьюнити и вовлечение
- рост (growth) и циклы распространения
- монетизация (стратегии, не “обещания”)

Цель семьи — сделать маркетинг системным: **что обещаем**, **кому**, **где**, **как измеряем**, и **как не ломаем канон**.

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
**FAMILY NAME:** MARKETING SPECIALISTS  
**FAMILY PATH:** `03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/10_MARKETING/`

### 2.1 Covered domains (what we DO)
- Brand system and narrative promise (Brand Architect)
- Audience analysis and segmentation (Audience Analyst)
- Audience research (qual/quant signals) (Audience Research Specialist)
- Content packaging (messages, hooks, formats) (Content Packaging Specialist)
- Distribution strategy and channel ops (Platform Distribution Specialist)
- SEO discovery (search intent, structure) (SEO Discovery Specialist)
- Trailer/teaser packaging (promise control) (Trailer & Teaser Specialist)
- Community operations (Community Manager)
- Engagement strategy (retention loops) (Engagement Strategist)
- Growth experiments (Growth Hacker)
- Monetization strategy (Monetization Strategist)

### 2.2 Hard boundaries (what we DO NOT do)
- Мы не создаём канон контента и не переписываем сюжет; мы упаковываем и доставляем.
- Мы не даём обещаний “гарантированного результата” и не делаем манипулятивные claims без оснований.
- Мы не принимаем релизные решения вместо `07_PRODUCTION/Release Manager`, но даём требования к упаковке/каналам.
- Мы не ломаем тон/мораль мира ради кликов — это S0 риск.

---

## 3) MESSAGE SAFETY (MANDATORY)
Любое публичное сообщение обязано:
- не противоречить канону
- не спойлерить, если spoiler gate запрещает
- не обещать невозможного/непроверяемого как факт
- иметь корректные рамки: “позиционирование” vs “факт”

---

## 4) KNOWLEDGE BASE (KB) SCOPE (MANDATORY)
### 4.1 KB INPUTS
- Marketing & Distribution realm  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/06__MARKETING_DISTRIBUTION.md
- Production Pipeline realm (release packaging + constraints)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/05__PRODUCTION_PIPELINE.md
- Reference Glossary realm (terminology hygiene)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/07__REFERENCE_GLOSSARY.md

### 4.2 KB OUTPUTS
- Библиотека “message packs”, “brand pillars”, “channel playbooks”.
- Стандарты “spoiler-safe promotion” и “promise control”.

### 4.3 KB BOUNDARIES
- Маркетинг не утверждает FACT без исследования/валидации.
- Любые численные/качественные заявления требуют источника или должны быть оформлены как позиционирование.

---

## 5) INTERFACES (SYSTEM LINKS) — RAW ONLY
### 5.1 Production interfaces
- Release Manager (execution partner)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/08__RELEASE_MANAGER_SPC.md
- Platform Adaptation Specialist (format constraints)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/06__PLATFORM_ADAPTATION_SPECIALIST_SPC.md
- Transmedia Producer (spoiler gates across media)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/07_PRODUCTION/04__TRANSMEDIA_PRODUCER_SPC.md

### 5.2 Research interfaces
- Research Director (claims policy)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/09_RESEARCH/01__RESEARCH_DIRECTOR_SPC.md
- Fact Checking Specialist (public claims gate)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/09_RESEARCH/07__FACT_CHECKING_SPECIALIST_SPC.md

---

## 6) FAMILY STANDARDS (MANDATORY RULES)
### 6.1 Anti-overlap (role separation)
- Brand Architect: бренд-скелет и обещание.
- Audience Analyst: сегменты и “кому что важно”.
- Audience Research Specialist: сбор данных и инсайты.
- Content Packaging Specialist: упаковка сообщений/структур.
- Platform Distribution Specialist: каналы и стратегия распространения.
- SEO Discovery Specialist: органическое обнаружение по поисковому намерению.
- Trailer & Teaser Specialist: упаковка обещания в трейлер/тизер (без спойлеров).
- Community Manager: операционка комьюнити.
- Engagement Strategist: удержание, петли вовлечения.
- Growth Hacker: эксперименты и масштабирование.
- Monetization Strategist: модели дохода/ценности (без “гарантий”).

### 6.2 Promise control law
Любое промо обязано иметь:
- “что обещаем” (promise)
- “что не обещаем” (non-promise)
- “что запрещено спойлерить” (spoiler gate)
- “какой CTA” (call-to-action)

### 6.3 Evidence law for claims
Если сообщение содержит факт (цифры/сравнение/объективное утверждение) — нужен:
- evidence note (источник) или
- downgrade в позиционирование/метафору (не FACT)

---

## 7) FAMILY NAV — SPECIALISTS (ORDER IS LAW)
01 — BRAND ARCHITECT  
02 — AUDIENCE ANALYST  
03 — AUDIENCE RESEARCH SPECIALIST  
04 — CONTENT PACKAGING SPECIALIST  
05 — PLATFORM DISTRIBUTION SPECIALIST  
06 — SEO DISCOVERY SPECIALIST  
07 — TRAILER / TEASER SPECIALIST  
08 — COMMUNITY MANAGER  
09 — ENGAGEMENT STRATEGIST  
10 — GROWTH HACKER  
11 — MONETIZATION STRATEGIST  

---

## FINAL RULE (LOCK)
Этот README задаёт границы семьи `10_MARKETING`.  
Если маркетинг ломает канон, спойлерит или выдаёт позиционирование как FACT — это S0 риск и должно блокироваться до исправления.

--- END.
