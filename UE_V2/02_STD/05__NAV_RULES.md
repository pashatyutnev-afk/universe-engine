# FILE: UE_V2/02_STD/05__NAV_RULES.md

SCOPE: UE_V2
LAYER: 02_STD
DOC_TYPE: STANDARD
MODE: REPO
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.V2.STD.NAV_RULES.001
OWNER: STANDARDS_OWNER
TITLE: NAVIGATION RULES (RAW-FIRST + RESOLVER)

---

## MARKERS
- [M] INTENT
- [M] DEFINITIONS
- [M] LAWS
- [M] RESOLVER_PROTOCOL
- [M] ANTI_GUESS
- [M] GATES

---

## [M] INTENT
Сделать навигацию детерминированной и “неубиваемой”:
- ассистент не гадает пути
- открывает файлы только по RAW
- допускает PATH только как ключ, если есть подтверждённый RESOLVER PATH→RAW

---

## [M] DEFINITIONS
- RAW_LINK: прямая ссылка на raw.githubusercontent.com (открывается без обходов)
- PATH_KEY: строка вида UE_V2/.../file.md (НЕ открывается напрямую в рантайме)
- RESOLVER: правило/таблица, которая однозначно переводит PATH_KEY → RAW_LINK
- CONFIRMED: PATH_KEY найден в LINK_BASE (или в другом утверждённом реестре PATH→RAW)

---

## [M] LAWS
L1) RAW-FIRST:
- Любой доступ к файлу в рантайме выполняется по RAW_LINK.

L2) PATH-ONLY-AS-KEY:
- PATH_KEY допускается только как “ключ-указатель”.
- Открывать файл по PATH_KEY запрещено.

L3) RESOLVER-REQUIRED:
- Если в IDX/NAV встречается PATH_KEY, ассистент обязан:
  (a) проверить наличие PATH_KEY в LINK_BASE (CONFIRMED)
  (b) получить RAW_LINK
  (c) открыть RAW_LINK

L4) NO-MASS-LOAD:
- Загружать только минимум: START + MANIFEST + ROUTER + NAV_ROOT + 1 доменный IDX + 1–3 таргет файла.

---

## [M] RESOLVER_PROTOCOL
R0) MUST_HAVE:
- в рантайме должен быть доступен минимум один утверждённый LINK_BASE (PATH→RAW)

R1) RESOLVE_STEP:
1) взять PATH_KEY
2) найти точное совпадение в LINK_BASE
3) извлечь RAW_LINK
4) открыть RAW_LINK

R2) FAILURE:
- если PATH_KEY не найден → STOP: RAW missing / resolver miss (без угадываний)

---

## [M] ANTI_GUESS
- Запрещено:
  - “примерно такой путь”
  - перебор директорий
  - частичный матч
  - догадки по названию

---

## [M] GATES
PASS если:
- каждый открытый файл был открыт по RAW_LINK
- каждый PATH_KEY был подтверждён через RESOLVER

STOP если:
- требуется файл, но RAW_LINK отсутствует и PATH_KEY не подтверждён
