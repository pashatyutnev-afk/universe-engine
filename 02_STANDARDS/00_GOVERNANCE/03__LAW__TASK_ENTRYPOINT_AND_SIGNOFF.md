# LAW — TASK ENTRYPOINT AND SIGNOFF
DOC_TYPE: LAW
SCOPE: Universe Engine
STATUS: ACTIVE
VERSION: 1.0.0

---

## RULE (ABSOLUTE)
Любая задача в системе начинается только через Top Governance диспетчера:
- GOVERNANCE_OWNER_SPC

Запрещено запускать работу напрямую через доменных специалистов, движки или оркестраторы, минуя диспетчера.

---

## REQUIRED FLOW
1) INTAKE (GOVERNANCE_OWNER_SPC)
2) DISPATCH (назначение исполнителей)
3) PRODUCTION (исполнение)
4) VERIFY (CTL/VAL/QA)
5) SIGNOFF (минимальный набор)
6) RETURN (выдача пользователю + фиксация ручных обновлений ссылок)

---

## MINIMUM SIGNOFF CHAIN
1) DOC_CONTROLLER_SPC — документ/формат/контроль версий и блоков
2) READINESS_CHECK_CTL — готовность артефакта к использованию
3) (опционально) доменный QA — качество/естественность/критерии домена

---

## MISSING ENTITY OBLIGATION
Если для задачи нет сущности нужного типа (SPC/ENG/ORC/CTL/VAL/QA/XREF) или нет KB-модуля:
- система обязана предложить создание сущности
- выдать шаблоны файлов
- указать регистрацию в реестрах
- пометить как “CREATED AFTER START — требует ручного обновления link base пользователем”

---

## LINK BASE NON-UPDATE
Link base (ROOT INDEX) не обновляется автоматически.
Любые новые пути/ссылки после выполнения работ — добавляются пользователем вручную.
