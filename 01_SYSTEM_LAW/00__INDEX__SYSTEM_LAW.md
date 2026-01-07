# SYSTEM LAW INDEX — MASTER REGISTRY (CANON)
FILE: 00__INDEX__SYSTEM_LAW.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
INDEX_TYPE: MASTER_LAW_REGISTRY
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Canonical navigation law + registry for all system-level laws (mandatory entrypoint)

---

## ROOT FILES (SYSTEM LAW LAYER)

00 — System Law (Core) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md  
01 — Naming Rules — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md  
02 — UID Rules — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md  
03 — Versioning & Change Policy — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md  
04 — Canon Protocol — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md  
05 — Artifact Schema Registry — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md  
06 — Constraints Registry — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md  
07 — Pipeline Registry — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md  

---

## 0) PURPOSE (LAW)
Этот INDEX — **единая точка истины** для всех законов слоя `01_SYSTEM_LAW`.

Он фиксирует:
- полный список LAW файлов
- строгий порядок применения (by number)
- канонические пути и raw-ссылки
- правило существования

### EXISTENCE RULE (ABSOLUTE)
> Если закона нет в этом INDEX — он **не существует** для слоя SYSTEM LAW.  
> Если файл есть, но не зарегистрирован здесь — **ignored / non-canon**.

---

## 1) HOW TO USE (MANDATORY FLOW)
1) Любой спор/вопрос по системе сначала сверяется с `00__SYSTEM_LAW.md`.
2) Затем открывается нужный LAW файл по номеру.
3) Любые новые LAW:
   - сначала добавляются в этот INDEX,
   - потом создаётся файл,
   - потом фиксируется change/version policy.

---

## 2) ORDER OF AUTHORITY (PRIORITY)
При конфликте законов приоритет такой:

1) `00__SYSTEM_LAW.md` (Core Law)
2) `04__CANON_PROTOCOL.md` (what is canon + how canon changes)
3) `03__VERSIONING_CHANGE_POLICY.md` (how changes are tracked)
4) `02__UID_RULES.md` (how system identifies things)
5) `01__NAMING_RULES.md` (how things are named)
6) `06__CONSTRAINTS_REGISTRY.md` (hard constraints)
7) `05__ARTIFACT_SCHEMA_REGISTRY.md` (artifact formats)
8) `07__PIPELINE_REGISTRY.md` (pipelines)

---

## 3) CANON MAP — SYSTEM LAW FILES

### 00 — SYSTEM LAW (CORE)
00 — System Law Core  
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md

### 01 — NAMING RULES
01 — Naming Rules  
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md

### 02 — UID RULES
02 — UID Rules  
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md

### 03 — VERSIONING + CHANGE POLICY
03 — Versioning & Change Policy  
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md

### 04 — CANON PROTOCOL
04 — Canon Protocol  
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md

### 05 — ARTIFACT SCHEMA REGISTRY
05 — Artifact Schema Registry  
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md

### 06 — CONSTRAINTS REGISTRY
06 — Constraints Registry  
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md

### 07 — PIPELINE REGISTRY
07 — Pipeline Registry  
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md

---

## FINAL RULE (LOCK)
> Этот INDEX — единственная точка истины о составе и порядке SYSTEM LAW.  
> Любая правка INDEX считается изменением канона и проходит canon protocol.

OWNER: Universe Engine  
LOCK: FIXED
