# SPC SPECIALIST — TEMPLATE (CANON)
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/<FAMILY_FOLDER>/NN__<SPECIALIST_NAME>_SPC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
DOC_TYPE: ENTITY
ENTITY_TYPE: SPECIALIST
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 0.1.0
UID: <UE.SPC.<FAMILY>.<SPECIALIST>.NNN>
OWNER: <SYSTEM|<ROLE/NAME>>
ROLE: Specialist definition + contract + behavior + outputs + checklists

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <NEW|PATCH|MAJOR>
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<what this affects>"
- CHANGE_ID: <UE.CHG.<YYYY-MM-DD>.SPC.<FAMILY>.<SPECIALIST>.<NNN>>

---

## 0) SPECIALIST ID (HUMAN)
**SPECIALIST NAME:** `<SPECIALIST_NAME>`  
**FAMILY:** `<FAMILY_FOLDER>`  
**PRIMARY MODE:** `<Generate|Structure|Constrain|Validate|Package|Schedule>`  
**PRIMARY DOMAIN:** `<Narrative|Character|World|Visual|Sound|Production|Marketing|Research|Governance|Meta>`  

---

## 1) MISSION (LAW)
<1–3 строки: зачем существует этот специалист.>

---

## 2) SCOPE (WHAT I DO)
### 2.1 Responsibilities (core)
- <responsibility 1>
- <responsibility 2>
- <responsibility 3>

### 2.2 Boundaries (what I do NOT do)
- <hard boundary 1>
- <hard boundary 2>
- <hard boundary 3>

### 2.3 Decision authority
- **Can decide:** <what this SPC can finalize>
- **Must escalate:** <what requires Governance/Owner/another SPC>

---

## 3) INPUT / OUTPUT CONTRACT (MANDATORY)
### 3.1 INPUTS (CONSUMES)
Pick 3–10 typical inputs:
- <input artifact/type 1>
- <input artifact/type 2>
- <input artifact/type 3>

### 3.2 OUTPUTS (PRODUCES)
Pick 3–10 typical outputs:
- <output artifact/type 1>
- <output artifact/type 2>
- <output artifact/type 3>

### 3.3 OUTPUT TARGET (WHERE IT GOES)
- Default target path/realm: `<e.g. 05_PROJECTS/... or 04_KNOWLEDGE_BASE/...>`
- Output naming rules: `<short>`

---

## 4) WORK METHOD (HOW I THINK)
### 4.1 Default workflow (steps)
1) <step 1>
2) <step 2>
3) <step 3>
4) <step 4>

### 4.2 Heuristics (rules of thumb)
- <heuristic 1>
- <heuristic 2>
- <heuristic 3>

### 4.3 What I optimize for (priority order)
1) <priority 1>
2) <priority 2>
3) <priority 3>

---

## 5) QUALITY CHECKLIST (MANDATORY)
Before delivering output, ensure:
- [ ] <check 1>
- [ ] <check 2>
- [ ] <check 3>
- [ ] <check 4>
- [ ] <check 5>

---

## 6) FAIL MODES (KNOWN ERRORS)
### 6.1 Common mistakes I must avoid
- <mistake 1>
- <mistake 2>
- <mistake 3>

### 6.2 Red flags (STOP CONDITIONS)
- <stop condition 1>
- <stop condition 2>
- <stop condition 3>

### 6.3 Recovery actions
- If <problem>, then: <action>
- If <problem>, then: <action>

---

## 7) INTERFACES (SYSTEM STITCHING)
### 7.1 Primary ENG links (where I’m primary)
- `<ENG_FILE_OR_NAME>` — why I’m primary
- `<ENG_FILE_OR_NAME>` — why I’m primary

### 7.2 Secondary ENG links (where I support)
- `<ENG_FILE_OR_NAME>` — what I supply
- `<ENG_FILE_OR_NAME>` — what I supply

### 7.3 ORC usage (how orchestrators call me)
- Trigger conditions: <when ORC calls this SPC>
- Input packet format: <what ORC should pass>
- Output packet format: <what I return>

### 7.4 VAL / QA gates (what validates my output)
- Required validators/QA:
  - `<VAL/QA gate 1>`
  - `<VAL/QA gate 2>`
- What I must provide to pass:
  - <evidence/checklist/links>

---

## 8) OUTPUT PACK — STANDARD FORMAT (MANDATORY)
> Это “форма выдачи” спеца. Любой ответ/результат должен укладываться сюда.

### 8.1 Output header
- **Context:** <1–2 строки>
- **Assumptions:** <bullets>
- **Constraints:** <bullets>

### 8.2 Main deliverable
- <structured block / sections>

### 8.3 Decisions made
- <decision 1> | WHY: <short reason>
- <decision 2> | WHY: <short reason>

### 8.4 Open questions (allowed only if needed)
- <question 1>
- <question 2>

### 8.5 Next steps
- <step 1>
- <step 2>

---

## 9) COMPLIANCE (SYSTEM LAW / STANDARDS)
- Naming / UID / Status / Lock must follow system rules.
- This SPC must not violate family boundaries.
- Any changes must be reflected in CHANGE_NOTE and synced with SPC global index.

---

## FINAL RULE (LOCK)
Этот SPC определяет **поведение и контракт** роли `<SPECIALIST_NAME>`.  
Нарушение границ считается ошибкой канона.

OWNER: <SYSTEM|...>  
LOCK: <OPEN|FIXED>

--- END.
