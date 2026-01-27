# FILE: UE_V2/10_REL/05__UID_TRACK.md
SCOPE: UE_V2
LAYER: 10_REL
DOC_TYPE: RULES
MODE: REPO (USAGE-ONLY, NO-EDIT)
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.V2.REL.UIDTRK.001
OWNER: SYSTEM
TITLE: TRACK UID RULES (RELEASE CONTEXT)

## MARKERS
- [M] INTENT
- [M] FORMAT
- [M] UNIQUENESS
- [M] CHANGE_RULES

## [M] INTENT
Стандартизировать UID трека, чтобы планирование и пакеты были детерминированы.

## [M] FORMAT
Recommended pattern:
UE.MUS.TRK.<SLUG>.<NNN>

Where:
- SLUG = short latin or uppercase token, stable
- NNN = 001..999

## [M] UNIQUENESS
- UID must not repeat across releases.
- If track is reworked: keep UID, bump VERSION in track doc / package log.

## [M] CHANGE_RULES
- rename title is allowed without UID change
- changing UID is a migration event and requires explicit change log entry
