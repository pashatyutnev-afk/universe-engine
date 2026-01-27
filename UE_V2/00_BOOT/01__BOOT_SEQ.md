# FILE: UE_V2/00_BOOT/01__BOOT_SEQ.md
SCOPE: UE_V2
LAYER: 00_BOOT
DOC_TYPE: RUNBOOK (BOOT SEQUENCE)
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.BOOT.SEQ.001
OWNER: SYSTEM

## MARKERS
- [M] GOAL
- [M] BOOT_STEPS
- [M] BOOT_TRACE_CONTRACT
- [M] BOOT_COMPLETE

## [M] GOAL
Сделать рантайм детерминированным: ассистент подтверждает, что знает законы, формат, стоп/гап, артефактность, минимальную сущностность и трассировку.

## [M] BOOT_STEPS
Порядок обязателен:
1) START loaded: UE_V2/00_BOOT/00__START.md
2) STOP vs GAP loaded: UE_V2/00_BOOT/02__STOP_GAP.md
3) CHAT format loaded: UE_V2/00_BOOT/03__CHAT_FMT.md
4) Artifact rule loaded: UE_V2/00_BOOT/04__ART_RULE.md
5) Minimal entities loaded: UE_V2/00_BOOT/05__MIN_ENT.md
6) Trace loaded: UE_V2/00_BOOT/06__TRACE.md
7) Fail codes loaded: UE_V2/00_BOOT/07__FAIL_CODES.md

## [M] BOOT_TRACE_CONTRACT
BOOT считается выполненным только если в текущем ответе в RESOURCES USED:
- перечислены загруженные документы (как ссылки или как V2_LOCAL refs)
- по каждому документу указан MARKER FOUND (конкретный [M] маркер)

Если хотя бы по одному документу маркер не подтверждён → STOP: marker not confirmed

## [M] BOOT_COMPLETE
BOOT COMPLETE, если подтверждено:
- EntryPoint law (single entrypoint)
- STOP vs GAP semantics
- Chat output contract
- Artifact-only rule
- Minimal entity usage rule
- Trace contract
- Fail codes set
