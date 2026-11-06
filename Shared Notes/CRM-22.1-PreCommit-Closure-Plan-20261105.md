# CRM 22.1 — Pre-commit closure plan (November 5, 2026)

**Status: GATE 1 AUTHORIZED BY ROB — EXECUTE ONLY WHEN ROB STARTS CODEX USING HIS NORMAL HANDOFF MESSAGE. GATES 2–6 REMAIN PLANNING ONLY.** This document records the one-at-a-time route to a reviewed source commit. Rob's November 5 verbal approval authorizes **only Gate 1**, a read-only source/diff reconciliation and its bounded documentation. It does **not** authorize source/test edits, source-workspace Git commands, builds, tests, GUI launches, package/transfer/deployment, operational-data access, or real email. Each gate ends with evidence and a STOP for Rob/Priya review; every later gate requires fresh explicit approval. Publication of this updated plan does not itself start Codex.

## Baseline — what is already known

- The November 5 A12/A02/A03/A09 completion report documents focused PASS: A12 6/6, A02 2/2, A03 4/4, A09 exporter class 15/15 (including the dedicated determinism test). The actual source edits are **local, unstaged, uncommitted, and unpushed**. Eleven paths were changed in that assignment, on top of previously preserved dirty work.
- No broad regression suite, standalone final Release build, real interactive CRM/Excel acceptance, source publication, package, or workplace validation was completed in that assignment.
- A12's reported workplace crash is **NOT VERIFIED**. A simulated successful-send boundary is **NOT RUN / not established**; removing premature draft-time FollowUp/date writes does **not** implement send-success date updates. A08 actual 125% and 150% Windows scaling is **NOT VERIFIED** from current published evidence; previous 100% observations do not substitute.
- Protect the Dev/isolated CRM 22.1 workspace and verify actual executable/build identity. Do not substitute the last merged version 22, or the older November 4 candidate ZIP, for the corrected working source.

## One gate at a time

### Gate 1 — Reconcile the real source and the complete dirty change set (READ-ONLY)

After Rob's normal explicit Codex start, read the **latest shared and CRM project handoffs**, this controlling plan, and the November 5 correction evidence. Verify Windows Dev identity, the intended local CRM 22.1 workspace/branch/source baseline, and the full tracked/untracked inventory using **read-only file-system and .git metadata inspection only**; do not execute Git/GitHub commands in the source workspace. Reconcile *all* accumulated pre-existing source/test edits plus the eleven November 5 changed paths against the authorized handoffs. Identify unexpected changes, missing files, source drift, dependencies and any unclear authorization. Record a concise per-file disposition with source paths, available hashes/identifiers and explicit PASS/FAIL/BLOCKED/NOT VERIFIED. **Do not build, run tests, launch the GUI, change display scaling or investigate unrelated defects.** Preserve all working files; do not reset, discard, overwrite, stage, commit, push, package or deploy. Confine any result writing to the existing authorized local handoff/report locations; no GitHub publication by Codex without separate authorization. End with a recommended smallest Gate 2 scope and **STOP**. **Pass:** one unambiguous reviewed source snapshot and authorized change inventory. **Fail/blocked:** document the exact discrepancy without guessing or broadening access.

### Gate 2 — Offline build and focused regression (separately approved execution)

On verified preserved source, run an isolated offline Release build with `CRMIncludeOperationalSeed=false`, then the directly affected test classes and appropriate established regression tests. Record exact commands, individual counts, failures, warnings, binaries and hashes, changed-file/integrity checks, and operational-seed/secret exclusion. If the broad suite is feasible and separately in scope, classify any failing cases as newly regressed, pre-existing, test-fixture, or environment-related using evidence; never call an unrun or failing suite PASS. Avoid speculative fixes and unrelated test maintenance. **Pass:** zero-error Release build and no unexplained material regression. STOP.

### Gate 3 — Interactive acceptance with fictional data only (separately approved execution)

Launch the **verified updated CRM 22.1 build**, not an older ZIP, against disposable fictional SQLite/settings/workbooks. Interactively verify A02 blank-contact-date clear/save/reopen and cancel; A03 clear/save/reopen/reactivate/replacement/shared-email behavior and preserved history; A12 draft create/resume/failure without operational FollowUp or Last Interaction/Last Follow-Up changes; A09 fresh and repeat exports, byte/SHA identity, no-data safety, and Excel-opened workbook/table/formula/style/unrelated-sheet behavior. Check database integrity, audit, no unintended writes, and isolation. **Never use live Graph, real email, workplace DB, or operational workbooks.** Record PASS/FAIL/NOT VERIFIED per case and capture reproducible evidence. STOP.

### Gate 4 — Separate A08 real GUI display-scaling acceptance (separately approved execution)

On the Windows 11 VM, verify the actual 22.1 executable and test **100%, 125%, and 150%** OS scaling. Record DPI/settings and screenshots, with pass/fail for relevant CRM and GoGreen forms. Include the entire GoGreen manual-override checkbox label, adjacent month/folder selector, action/status controls, and restored/maximized/narrow layouts; inspect clipping, overlap, readability and access. Restore the original Windows scaling at the end and verify restoration. No changes to product code, Git, email, or production data in this gate. If desktop settings cannot safely be changed, mark each unrun scale **NOT VERIFIED** rather than PASS and STOP with exact blocker. If a defect appears, propose only the smallest correction for separate approval.

### Gate 5 — Consolidated acceptance and commit decision (READ-ONLY review)

Reconcile Gates 1–4, initial/final hashes, all PASS/FAIL/NOT VERIFIED evidence, pending defects, and source change scope. Distinguish:
- **Commit blockers:** unreviewed/unexplained source changes, broken build, confirmed material regression, failed mandatory UI/data-integrity check, or required acceptance left unresolved without an explicit Rob decision.
- **Explicitly deferred/non-claimed:** office-only live Graph/email testing, successful-send-only date behavior until a real verified send boundary exists, unverified reported workplace crash pending diagnostic evidence, and any other unrelated feature ideas. Do not claim those fixed or accepted. Their potential **release** implications require a separate Rob decision even if the bounded source changes are commit-ready.
- **Package/release blockers:** any required workplace acceptance and delivery checks not yet passed.

**Commit-ready** means the reviewed bounded changes are consistent, buildable and regression-checked, with all unresolved exceptions disclosed and accepted by Rob. It does **not** mean the application is deployed, email-tested, or release-ready.

### Gate 6 — Controlled source commit ONLY after separate explicit Rob authorization

When Rob approves the Gate 5 source inventory and the exact commit scope, use only the approved source branch/workspace and explicitly reviewed files. Confirm no production databases, seeds, credentials, logs, recovery/backup data, output artifacts, or unrelated files are staged. Create the reviewed source commit only within the later permission scope; verify what actually committed. Push, merge, package a Friday test ZIP, transfer, deploy, release, or use live services **only under distinct authorization**. Do not interpret “get it ready to commit” as permission to run Git now.

## Failure and handoff rule

At each gate, document exact tested identity, evidence, failures/blockers, minimum safe follow-up and STOP. Investigate a failure within approved scope; continue unaffected work only if separately allowed and safe, and do not auto-escalate to new fixes. Keep one authoritative concise status in the established current handoffs, preserve history, and record oversized handoffs rather than reorganizing them without authorization. **Current authorization: Rob approved Gate 1 only. Run it only after his normal Codex start; no Gate 1 execution is claimed by this documentation update. After the read-only inventory report, STOP for Rob/Priya review. No Gate 2–6 execution without new authorization.**

## Source evidence

- [November 5 authorized correction handoff](CRM-22.1-Nov05-Corrections-Authorized-20261105.md)
- [November 5 completed correction report](CRM-22.1-Nov05-Corrections-Completed-20261105.md)
- [November 5 consolidated investigation](CRM-22.1-Nov05-Consolidated-Investigation-Completed-20261105.md)
