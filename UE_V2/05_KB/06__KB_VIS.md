# FILE: UE_V2/05_KB/06__KB_VIS.md
SCOPE: UE_V2
LAYER: 05_KB
DOC_TYPE: KB_DOMAIN
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.KB.VIS.001
OWNER: SYSTEM
TITLE: KB VISUAL (AUDIO→VIS MAP)

## MARKERS
- [M] DEFINITIONS
- [M] MAPPINGS
- [M] CONSTRAINTS

## [M] DEFINITIONS
- ID: VIS.ZP | TYPE: DEF | BODY: “Zero Point” визуальный режим: белая точка на чёрном фоне, минимум движения, максимум внимания.
- ID: VIS.GLT | TYPE: DEF | BODY: “Glitch artifacts” = короткие сбои, синхронизированные с транзиентами/пиками, без разрушения сцены.

## [M] MAPPINGS
- ID: MAP.CF.GLITCH | TYPE: MAP | BODY: если CF_3s_P50 > 14 dB → активировать GLT пакет (микро-сбои, 1–3 кадра, на транзиентах).
- ID: MAP.LRA.ZP | TYPE: MAP | BODY: если LAW-13 активен и RMS drop >= 12 dB → VIS.ZP на интервал “вакуумной тишины”.
- ID: MAP.AIR.DOF | TYPE: MAP | BODY: энергия 8–16 kHz ↑ → прозрачность/DOF ↑; энергия ↓ → матовость/дымка ↑.

## [M] CONSTRAINTS
- ID: CST.CONTINUITY | TYPE: CST | BODY: один персонаж/локация/световой сетап в пределах сцены, если не указана смена по пайплайну.
- ID: CST.NO_TEXT | TYPE: CST | BODY: запрет читаемого текста/логотипов/сабов в окружении (кроме явно разрешённых оверлеев).
