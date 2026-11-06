# CRM 22.1 — November 5 Correction Handoff

**Status:** Authorized by Rob for Codex execution. No fixes, builds, or deployment authorized by publication alone.

## 1. Authority and environment
Read the completed November 5, 2026 CRM 22.1 consolidated investigation report and the authoritative current and historical handoffs. Verify the actual isolated CRM 22.1 maintenance workspace, Dev account, intended branch, source baseline, existing changes, and dependencies before editing. Preserve pre-existing modifications; never discard changes to establish a clean baseline. If the intended source or baseline cannot be established reliably, STOP and report.

## 2. Authorized scope
Narrowly scoped source and test corrections for A12, A02, A03, and A09, in that order. No unrelated functionality. Do not access or modify production databases, backups, USB or Z: operational copies, recovery files, real mailboxes, or deployed applications. Use fictional data and disposable databases. No live Graph calls or actual email sends. No application packaging, deployment, branch merging, or Git/GitHub commands or publication.

## 3. Sequential execution
For each issue: review evidence and code; identify smallest reliable correction; implement only justified edits; add/update focused tests; execute and record tests; verify correction and relevant regressions; record PASS, FAIL, BLOCKED, or NOT RUN with evidence. PASS requires all required tests to pass. Do not claim unexecuted tests passed.

### A12 — Draft-related dates
Remove operational FollowUp Activity, Last Interaction, Last Follow-Up, and associated draft-follow-up ledger writes from draft creation and reconciliation paths. Preserve legitimate draft audit, identification, duplicate prevention, and resume behavior. Correct misleading UI text. Test draft create, duplicate/resume, cancellation, verification failure, and simulated Graph failure: none may change operational dates or follow-up records. Do not introduce a new send workflow. Simulated successful-send tests may exercise only an existing verified success boundary; otherwise mark NOT RUN. Do not modify historical workplace dates. Reported crash remains unverified; do not invent a fix.

### A02 — Contact date clearing
Correct nullable date-picker notifications so mouse and Delete/Backspace clearing update the bound value without triggering events during programmatic load. Test clear/save/reload, cancel, and replacement dates. Verify SQL NULL persists.

### A03 — Contact email clearing
Clearing an email must deactivate the applicable method without deleting its history. Re-entering the same normalized value must reactivate the existing method rather than insert a duplicate. Preserve primary/display rules. Test clear/save/reload, cancel, reactivation, replacement, shared-email warnings, phone methods, audit records, and transaction rollback. Do not alter unrelated contacts.

### A09 — Excel byte consistency
Preserve SHA-256 byte-identity requirement for identical input and workbook state. Investigate first-save XML and ZIP timestamp differences; implement smallest reliable deterministic XLSX serialization. Test fresh export, repeated update, hashes, visible values, formulas, tables, styles, unrelated sheets, and failure recovery. Never weaken acceptance criteria. If substantial restructuring is needed or validation is unreliable, document blocker and proposal rather than expand scope.

## 4. Failure handling
For a failure, capture evidence, investigate within scope, apply another correction only when its cause and safety are established; otherwise mark FAIL/BLOCKED, propose smallest reliable fix, and continue to the next independent unaffected issue when safe. No speculative retry loops. Stop affected work if shared infrastructure, source integrity, test reliability, or database safety is compromised. Identify dependencies; do not let earlier failures invalidate later test results. Preserve unsuccessful edits and evidence; do not silently reset or overwrite.

## 5. Verification
Run focused tests per issue and applicable existing regression suite after authorized changes. Fictional disposable data only. Record commands, test counts, errors, and results; distinguish current from historical evidence. Inspect modified file scope. Unrun tests are NOT RUN or BLOCKED, never PASS.

## 6. Documentation
Produce one consolidated completion report: per-issue results, root causes, corrections, exact changed files, tests and evidence, remaining defects and proposals, source baseline/integrity, regression risks, limitations, and recommendation for Friday's test ZIP. Update local current and historical handoffs without overwriting prior entries. Do not reconstruct missing evidence or replace full reports with summaries. Record files approaching 500,000 bytes; do not reorganize oversized history in this assignment.

## 7. Publication boundary
No Git/GitHub commands, commits, pushes, merges, rebases, resets, force operations, or publication. Local documentation updates only in verified workspace. Report exact paths and publication status; request separate authorization for GitHub publication. Local completion is not GitHub publication.

## 8. Final STOP
Do not package Friday's test ZIP, deploy, change production records, or send real email. Return consolidated report and STOP for Rob/Priya review. No further development, packaging, deployment, or data correction is authorized.
