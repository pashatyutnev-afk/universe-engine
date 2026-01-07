# REL POLICY + XREF — STANDARD
FILE: 02_STANDARDS/06_MARKING_STANDARDS/05__REL_POLICY_XREF.md

SCOPE: Universe Engine / Linking & Dependencies
LEVEL: L1
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0
OWNER: SYSTEM
ROLE: Единый стандарт: (1) кто с кем может связываться, (2) как оформляются ссылки и зависимости.

SOURCE OF TRUTH:
- REL_POLICY, XREF, DEPENDS_ON, PRODUCES_LINKS, CONSUMES_LINKS — описаны здесь.

---

## 0) CORE LAW
- Любая реальная зависимость должна быть явной: `DEPENDS_ON`.
- Любая ссылка на объект должна указывать его `ID`.
- Скрытые зависимости запрещены.
- Нарушение REL_POLICY (NEVER) = S0.

---

## 1) REL POLICY (WHO MAY LINK TO WHOM)
REL_POLICY задаётся в паспорте объекта (ENG/SPC/ENT/ART/DB/…).

### 1.1 Modes
- ALWAYS — разрешено всегда
- SOMETIMES — разрешено при условиях
- NEVER — запрещено

### 1.2 Format (canonical)

REL_POLICY:
  - TARGET: "<selector>"
    MODE: "ALWAYS|SOMETIMES|NEVER"
    CONDITIONS: "<only for SOMETIMES or empty>"
    REASON: "<why>"
1.3 TARGET selector rules
TARGET может быть:

по PREFIX: ENT:*, ART:*, DB:*, LOG:*, ENG:*, SPC:* …

по TYPE: ENT:CHR:*, ART:SCENE_STACK:* …

по конкретному ID: ENT:SCENE:ep01_scn_003

2) LINK TYPES (все связи стандартизированы)
2.1 Structural links (navigation)
XREF — одиночная ссылка

XREFS — список ссылок
Назначение: “см. также”, навигация, привязки без обязательности.

Формат:

XREF: <ID>

XREFS: [<ID>, <ID>, ...]

2.2 Dependency links (required to build)
DEPENDS_ON — обязательные зависимости (сборка невозможна без них)

Формат:

DEPENDS_ON: [<ID>, ...]

если нет: DEPENDS_ON: []

2.3 Production links (inputs/outputs)
CONSUMES — типы входов (не ссылки)

CONSUMES_LINKS — конкретные входные ID

PRODUCES — типы выходов (не ссылки)

PRODUCES_LINKS — конкретные выходные ID (если уже известны)

Формат:

yaml
Копировать код
CONSUMES: ["<type>", "<type>"]
CONSUMES_LINKS: ["<ID>", "<ID>"]
PRODUCES: ["<type>", "<type>"]
PRODUCES_LINKS: ["<ID>", "<ID>"]
3) VALIDATION (что считается ошибкой)
S0:

DEPENDS_ON указывает на объект, который нарушает REL_POLICY (NEVER)

DEPENDS_ON содержит невалидный ID

DEPENDS_ON используется как “см. также” (для этого XREF)

S1:

есть XREF, но нет смысла/описания контекста (пустая связь)

4) MINIMUM REQUIRED (для разных документов)
ENG/SPC должны иметь: DEPENDS_ON, CONSUMES, PRODUCES

ENT:SCENE должен иметь STACK_REF (см. SCENE_STACK стандарт)

ART артефакты должны иметь DEPENDS_ON если зависят от пакета/сцены/шота

END.