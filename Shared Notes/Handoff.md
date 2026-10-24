# Current Shared Handoff — Active Control

**Updated:** October 23, 2026. **State:** two-file handoff transition only. No CRM execution or migration is authorized by this document update.

## Read order and authority
1. Read this ENTIRE file and applicable repository `AGENTS.md` before acting. Read the current project-specific CRM `HANDOFF.md` and precisely cited historical sections when an assignment requires them; if any required material is truncated, STOP.
2. Historical material in [Handoff-history.md](Handoff-history.md) is reference/evidence, NOT authorization. Old headings such as NEXT or PENDING EXECUTION do not authorize tasks. Conflicting or unclear instructions require Rob's explicit clarification.
3. Only a newly and explicitly approved, bounded task may execute. Reporting, document review, and handoff changes never imply permission to launch CRM, run tests, modify a database/settings, change security, access Graph/mail, merge, package or deploy.
4. On completion, preserve results and unresolved findings in history before replacing the active assignment; verify the archived content, commit and remote file before shortening the current handoff. Never silently drop restrictions, exceptions or outstanding items.

## Active work and authorization
**CURRENT TASK: Handoff structure transition — documentation only.** Rob approved reorganizing the shared handoff into a compact active file and complete history. The original `Shared Notes/Handoff.md` (blob SHA `755072c9076f2fe3058baad4104ae9dfc958627d`) was copied verbatim into `Shared Notes/Handoff-history.md`, following its archive header. The archive is the full record, not a request to rerun old work. The current project-specific handoff remains separately controlling for CRM-specific restrictions.

**NEXT POSSIBLE TASK — NOT AUTHORIZED:** CRM Test 22 real historical Test20 settings migration, using only verified disposable copies after confirming exact legacy source and isolation. This is separate from ordinary GUI Save/restart persistence, USB-currentness, and database copy/parity stages. Do not start it based on this note; wait for Rob's separately approved instructions and reconcile with the latest project handoff. The October 23 reviewed data-transition proposal in history states that Stage 1 read-only source-currentness preflight is its next proposed step, with later stages unapproved. If the proposed settings task conflicts with that sequence, STOP and obtain Rob's decision.

## Current CRM Test 22 facts and unresolved gates
- The October 20 Test20 Z-drive backup is a verified historical schema-24 snapshot: 7,404 rows in 35 user tables; it is NOT proof of the newest USB database. VM lacks USB access. Never silently substitute an older source or access protected originals.
- Logical comparison/integrity of prior disposable database evidence passed; a target physical SHA-256 mismatch remains a recorded FAIL. Do not recategorize it as PASS. WAL/SHM attribution remains NOT VERIFIED.
- Automated normal shutdown/PID exit previously failed or was not demonstrated; Codex native GUI feasibility failed before CRM launch on October 23. Keep those outcomes distinct. Rob plans later manual normal close, Task Manager PID check, reopen, and settings/database persistence verification; no automated launch is approved here.
- The historical Test20 CRM settings source and ordinary legacy-to-stable import remain NOT VERIFIED. Fictional 16-value settings migration passed but does not prove real settings import; `CRM_SETTINGS_PATH` override bypasses the normal legacy import. Stable `%LOCALAPPDATA%\DeltaTrak\CRM\settings.json` precedence must be respected.
- Three business decisions remain pending Rob: Site 246 address, RecycleProgramProfile 274 Notes removal, ContactMethod 759 IsPrimary. No automatic edits or disclosure of private field values in handoffs.
- Graph/email, real production profile/USB/Z-drive writes, migration, application launch, ACL/identity/guard changes, merges, packages, deployments and daily cutover are NOT authorized. A Graph-disable flag alone is not proof of network isolation.
- Preserve rollback and newer data. October 19 recovery had 7,393 rows versus October 20 Test20 backup's 7,404 (11 additional rows and 22 changed rows, zero removals). Source currentness must be established before any future copy/migration.
- Earlier project-level October 23 reviewed proposal is DOCUMENTATION ONLY; stages 1–5 require separate approval and STOP gates. The T22-MSP-01 GUI attempt stopped at feasibility before CRM launch; later UI stages NOT RUN.

## Archiving / writeback protocol
At the end of each *authorized* assignment, record exact scope, date, branch/commit, PASS/FAIL/NOT VERIFIED/NOT RUN evidence, exceptions, pending Rob decisions, and next proposed step in history. Preserve historical failures. Verify the archive on GitHub before replacing this file's active section. Keep this file concise, retaining permanent safeguards and open blockers. Project handoff writeback is only permitted when the assignment authorizes it. Verify actual remote commits and content; report any partial failure honestly. STOP after the assigned scope.

## History pointer
Full pre-transition shared handoff (all 3,226 original lines): [Handoff-history.md](Handoff-history.md). Consult only specific relevant historical entries, except when a task explicitly requires a full historical audit. Original archived source blob: `755072c9076f2fe3058baad4104ae9dfc958627d`.
