# CRM 22.1 — Three-stage maintenance review completed

Date: 2026-11-04  
Status: **COMPLETE within the authorized three-stage boundary; NOT PACKAGE READY; STOP for Rob/Priya review.**

## Authority and preserved boundary

Executed only `CRM-22.1-Three-Stage-Maintenance-Review-Authorized-20261104.md`. Preflight passed as `DESKTOP-UH85JC0\Dev` in the existing `C:\Users\Dev\CRM-22.1-Maintenance-20261103` worktree on `codex/crm-22-1-maintenance-20261103`, remote `DarkPiglet/Weekly-Logger-Search-Application`. The verified source baseline remains commit `dd223e6f228c236c85b89b1246b587b2a0d1f5c2`, tree `0bfca6c87411c5f8129e35bfde28dc987c954af8`. The documented modified and untracked source/test inventory matched before and after all three stages and remains unstaged, uncommitted and unpushed.

No source or test file was edited, staged, committed or pushed. No application, interactive GUI, Excel automation, display-scale change, live Graph/email/carrier operation, operational/customer/production/recovery database, real settings/profile, USB, `Z:`, P2/P3, package, merge or deployment was used. Only the approved fictional fixture copy and confined generated test output were written in Stage 2. Documentation-only publication is the sole repository change.

## Stage 1 — maintenance reconciliation COMPLETE

The full item-by-item reconciliation is in `CRM-22.1-Three-Stage-Review-Stage1-Reconciliation-Completed-20261104.md`.

- **VERIFIED COMPLETE:** order-form review/publish/replacement behavior; UPS/FedEx parity; Graph-ID display suppression with retained underlying data; Site Information editor; Contact cards after the targeted validation/menu fixes; Quick Lookup after matched-contact context/highlight/scroll fixes; current possible-duplicates scan/confirmed-merge surface.
- **PARTIAL:** GoGreen layout is accepted at actual 100% only; actual Windows 125% and 150% remain separately **NOT VERIFIED** and excluded. Alias edit/save/reopen works, but the Alias textbox still lacks the explicit fixed border used by Street Address and read-only/text contrast parity is not accepted. Smaller UI/Settings notes do not establish one bounded defect; broad regrouping/redesign remains deferred.
- **IMPLEMENTED BUT UNVERIFIED at Stage 1:** RC Log and Agreement export functions. Their selected offline behavior was then tested in Stage 2.
- **NOT STARTED:** RC Log/Agreement readability formatting. The exporter does not add AutoFit/explicit widths, wrapping or a date-format normalization pass; existing tests only preserve established formats such as amount/date cells.
- **DEFERRED:** office-only email/Graph testing; successful-send-only interaction/follow-up timestamp semantics; advanced search grammar; customer acknowledgement; actual 125%/150% scaling; whole-app/Settings redesign. These are not PASS and were not authorized for implementation.

The prior broad UI result remains **139 passed / 27 failed / 166 total**, not a product PASS and not 27 proven product defects. Many failures require the intentionally absent output seed; remaining timeout/layout results are case-specific. The former company-button helper failure is superseded by the later focused `Form1SmokeTests` 6/6 PASS, but that does not reclassify the broad run.

## Stage 2 — bounded isolated automated regression COMPLETE with failures and blocks

### Isolation and command route

A fresh ignored disposable root was created at:

`C:\Users\Dev\CRM-22.1-Maintenance-20261103\artifacts\CRM22.1-ThreeStageReview-20261104\Run-01`

Only the approved wholly fictional schema-24 fixture was copied to isolated test output as `Binaries\Ui\Database\CRM_seed.sqlite`. Source and copied fixture SHA-256 both remained `0EFDF5FD7BEB5E445CE344D2A5460153E6F3EE0F956A723CC7E330D5837C43A7`. The tracked operational seed was hash-checked only and remained `3363942E28E35C3F19E3B502CDB528FF8D2D1051B70025C656EE66420D51E4A9`; it was not opened, copied or used. The retained Stage 3 Run-01 database remained `6EF0DC0155A0C959B50C4591E07BA21E6C3C124D0899C694EDE8A49AB1FF51B9` and its seed remained `0EFDF5FD...3C43A7`.

The run used the already-built UI test assembly copied under the disposable root and `dotnet vstest` with an explicit seven-test selection. `TEMP`, `TMP`, `DOTNET_CLI_HOME`, `USERPROFILE`, `LOCALAPPDATA` and `APPDATA` were confined beneath the run root; telemetry was disabled and HTTP/HTTPS proxies were pointed to closed loopback. No restore, network dependency, GUI or Excel was used. The first invocation had a malformed results-directory argument and started no tests; it only created .NET first-run files, including a development certificate, inside the disposable profile. The corrected invocation then ran exactly the selected cases.

### Results

**UI exporter selection: 7 total — 4 PASS / 3 FAIL / 0 skipped.**

PASS:

- `InvalidSecondWorkbookLeavesFirstWorkbookUnchanged`
- `ExportCanCreateOnlyTheConfiguredWorkbook`
- `InvalidExistingSecondWorkbookDoesNotCreateNewFirstWorkbook`
- `ValidationRejectsDuplicateAndInterleavedExportHeaders`

FAIL:

- `ExportCreatesBothWorkbooksWhenConfiguredFilesDoNotExist`: the fictional fixture has zero Agreement rows; the exporter correctly reports zero but the generated Excel table retains one blank data row, so the assertion expected last row 1 and observed 2.
- `ExportReplacesOnlyTargetTableRowsAndIncludesOnlyActiveRecords`: the same zero-row table representation produced expected last row 3 versus observed 4.
- `ReorderedContiguousExportTableIsMappedByHeaderAndPreservesOutsideFormula`: fixture/precondition failure at `.First()` because the approved fictional fixture has no Agreement export row; this is not product-failure evidence.

The two zero-row failures establish a real workbook/test-contract mismatch: `WriteRows` intentionally resizes to at least the first data row, while the assertions expect a header-only table. The visible blank row may be an acceptable Excel-table constraint or may require a product/test correction, but it is not resolved by this review. Smallest next step: decide the required zero-row workbook representation, then correct either the exporter or the two assertions and rerun only those cases. For the reordered-table case, create its own wholly fictional agreement row or explicitly skip/guard the zero-row precondition, then rerun that one case.

The requested data-maintenance selections — `DuplicateScanAndConfirmedMergeOperationsPreserveRelationships` and `CrossCompanySiteMergeRollsBackWithoutChanges` — are **BLOCKED / NOT RUN**. No prebuilt `CRM.Data.Tests.dll` existed in the approved isolated route. Building/restoring it would have created additional intermediates outside the already verified path or required broader dependency work, so the assignment correctly stopped rather than expanding access. This is 0 PASS / 0 FAIL / 2 BLOCKED for that selection.

TRX evidence: `Run-01\Results\Stage2-Exporter.trx`, SHA-256 `90949834FADAA714EB7A939B45B68BD67474ABC2303285BE703758E5749EAFA3`.

Post-run containment passed: 180 files / 89,631,835 bytes, zero reparse points, exactly one SQLite file with the fictional hash, zero operational-seed hash matches, no active CRM/GoGreen/Excel/testhost process, all protected/retained hashes unchanged, and dirty source/test inventory unchanged.

## Stage 3 — accumulated change-integrity review COMPLETE

Read-only inspection covered every modified/untracked application and test path against the verified baseline and all four authorized implementation scopes.

### Confirmed integrity findings

- **Scope mapping PASS.** Every accumulated path maps to operational-seed exclusion, order-form safety, UPS/FedEx parity, GoGreen layout, Site Information, Contact cards, Quick Lookup/History, or their focused tests. No unrelated feature, schema or broad refactor was found.
- **Business/suppression rules PASS by static comparison.** GoGreen defaults remain Boxes 30 days and Labels 14 days; validation remains 0–90; the manual override path and applicable-activity selection remain unchanged. The only GoGreen source diff is the authorized AutoSize layout change.
- **Mappings/nullable dates/transactions PASS by static review.** Site Information preserves Receiving, Preferred Carrier and all six activity mappings; hidden DT Associate round-trips without a visible ownership edit. Nullable dates retain blank/delete behavior. Contact cards use the existing `BindingSource`/`DataRowView` identities and fields. Save validation occurs before `EndEdit`; repository writes and all six `SetLatestSiteActivity` calls remain inside the existing `BeginBatch`/`Commit` boundary.
- **Audit/history/data protection PASS by static review plus prior interaction evidence.** UPS/FedEx actions retain site/contact association and activity types; Graph-ID lines are removed only from rendered History while raw details remain stored/searchable. Order-form generation/publish keeps same-volume staging, atomic replacement/rollback and no activity on pre-approval failure. The seed include properties default on for production and are conditional off for isolated build/test routes. No dependency, package reference, connection string, credential or secret drift was found.
- **Diff hygiene PASS.** `git diff --check` returned no errors. The final modified/untracked path inventory exactly matches preflight.

### Confirmed gaps, risks and unverified concerns

1. **P2 — zero-row Agreement workbook contract unresolved.** Two selected tests fail as described above. This blocks claiming the exporter regression selection green, even though rollback/single-target/layout validation cases passed.
2. **P2 — export readability formatting not implemented.** Column width/AutoFit, wrapping and systematic date formatting remain the smallest clearly outstanding original maintenance item.
3. **P2 — duplicate-integrity runtime verification blocked.** The actual implementation was previously accepted, but the two selected relationship/rollback cases did not run here. Establish a separately approved prebuilt/offline data-test route before relying on this review as fresh regression evidence.
4. **P3 — Alias presentation partial.** Edit/save behavior is verified, but border and read-only/text contrast parity remain a small bounded presentation correction/verification candidate.
5. **Acceptance gap — GoGreen actual 125%/150%.** Still NOT VERIFIED and explicitly excluded from this assignment.
6. **DEFERRED — successful-send-only date semantics.** The current box-order activity is recorded immediately after approval/publish and before email outcomes. This known draft/approved-versus-sent question remains deferred; it is not a newly authorized defect fix or live-test request.
7. **Unverified concern — Excel discovery gate.** `Form1` still checks registry/common executable paths before creating Excel through COM. It passed the authorized actual 100% host test, but installations available through COM yet absent from those paths could be rejected. Treat as a portability concern, not a confirmed defect.
8. **Unverified concern — visual-state interaction.** Quick Lookup clears control backgrounds to `SystemColors.Window`; no regression was observed in the targeted interaction, but read-only/validation-color coexistence is not comprehensively accepted.

No source correction was made for any item above.

## Readiness decision and STOP

All three authorized stages are complete. The accumulated worktree is **NOT PACKAGE READY** because source/test changes remain intentionally uncommitted, the selected exporter run is 4/7 rather than green, two duplicate-integrity tests are blocked, export readability and Alias presentation remain open, actual 125%/150% is not verified, and there is no package/merge/deployment authorization.

Smallest justified next work, only after separate Rob authorization, is: (1) resolve the zero-row Agreement workbook contract and the reordered-test fixture precondition; (2) provide a verified offline prebuilt route for the two data-maintenance tests; (3) implement/verify the narrowly defined export readability formatting; (4) decide whether the Alias border/contrast difference warrants correction; and (5) perform separately authorized actual 125%/150% checks. Do not combine these with deferred office email/send-success semantics or a broad UI/Settings redesign.

**STOP for Rob/Priya review. No fix, new phase, package, merge or deployment starts automatically.**
