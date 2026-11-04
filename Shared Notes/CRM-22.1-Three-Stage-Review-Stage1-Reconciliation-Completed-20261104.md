# CRM 22.1 — Three-stage review, Stage 1 maintenance reconciliation completed

Date: 2026-11-04

Status: **Stage 1 COMPLETE. Documentation-only reconciliation; no application/test source change and no test or application execution. Proceed to the authorized Stage 2 only under its isolation gates.**

## Authority and preflight

Executed Stage 1 of `CRM-22.1-Three-Stage-Maintenance-Review-Authorized-20261104.md`, incorporating the read-only `CRM-22.1-Post-Stage3-Maintenance-Reconciliation-Authorized-20261103.md`. Actual execution identity is `DESKTOP-UH85JC0\Dev`; workspace, remote and branch are `C:\Users\Dev\CRM-22.1-Maintenance-20261103`, `DarkPiglet/Weekly-Logger-Search-Application`, and `codex/crm-22-1-maintenance-20261103`. The documented source baseline remains `dd223e6f228c236c85b89b1246b587b2a0d1f5c2` / tree `0bfca6c87411c5f8129e35bfde28dc987c954af8`. The exact expected dirty source/test inventory matched the November 4 handoffs. All edits remain unstaged, uncommitted and unpushed.

The current shared/project handoffs, both `AGENTS.md` files, controlling three-stage authorization, original reconciliation authorization, November 4 Stage 3 completion report and direct November 3 maintenance/Stage 1/Stage 2 reports were read. The permanent history index was consulted only to confirm that current November 3–4 records are the appropriate evidence; no numbered volume was needed. No test, build, executable, database or Excel operation occurred in Stage 1.

## Reconciled maintenance register

| Item | Status | Evidence and remaining risk | Minimum next step |
|---|---|---|---|
| A. Order-form new/same-name publication and failure preservation | **VERIFIED COMPLETE** | November 4 actual Excel re-test opened the staged workbook, created a new file, safely replaced the same name, and retained the original byte/hash under a forced destination lock with no false BoxOrder activity. Existing atomic staging/replacement code remains in the dirty worktree. | Preserve in the Stage 3 integrity audit; no redundant rerun. |
| B. UPS parity with FedEx | **VERIFIED COMPLETE** | Stage 3 interactively recorded FedEx label/pickup and UPS label/pickup against loopback, with correct activity types, dates/details and Company/Site/Contact association; reopen persisted. | Static integrity review only. No live carrier test. |
| C. GoGreen manual-override layout | **PARTIAL** | AutoSize layout is implemented. Actual 100% Windows scaling passed restored, narrow and maximized, including Settings. Actual 125%/150% remains **NOT VERIFIED** and is explicitly outside this assignment. | Separate manual 125%/150% authorization and checklist already documented; no DPI change now. |
| D. Hide Graph ID from History display | **VERIFIED COMPLETE** | Interactive History and focused regression suppressed labeled Graph-ID lines while retaining raw stored/searchable details. No Graph call occurred. | Preserve hidden-storage/display boundary in Stage 3 review. |
| E. Site Information controls | **VERIFIED COMPLETE** | Stage 3 fictional interactive cancel/save/reopen, null-date preservation, correct SiteUpdated audit and absence of unintended date activity passed. All six date mappings and hidden DT Associate round-trip are documented. | Static mapping/transaction audit only. |
| F. Contact Information cards | **VERIFIED COMPLETE** | Add/edit/cancel/delete/reopen and audits passed in Stage 3; November 4 targeted re-test then passed explicit blank-name validation/focus and on-screen Actions placement. | Static DataView/BindingSource/audit review only. |
| G. Quick Lookup presentation | **VERIFIED COMPLETE** | November 4 interactive search showed contact context, exact green field highlight, selected/scrolled card; automated source-tooltip/context checks passed. Existing matching grammar was not expanded. | Static no-write/normalization review only. |
| Alias editor behavior | **PARTIAL** | Editable `TextBox`, 100-character limit, save/reopen and audit behavior are verified. Presentation parity is not complete: `txtStreetAddress` explicitly uses `BorderStyle.FixedSingle`, while `txtAlias` has no matching border assignment and retains default TextBox/read-only appearance. Text contrast parity was not directly accepted. | Separately authorize the smallest designer-only border/read-only contrast correction plus visual check. |
| RC Log and Recycle Agreement export function | **IMPLEMENTED BUT UNVERIFIED in this review** | Existing code safely maps headers, preserves unrelated workbook content/formulas and existing formats, supports one/both targets and rollback. Stage 1 did not rerun tests. | Stage 2 may run only the non-GUI, non-Excel-automation exporter tests using a fresh copy of the proven fictional fixture. |
| RC Log and Recycle Agreement readability formatting | **NOT STARTED** | `CRMWorkbookExporter.UpdateWorkbook` writes values and resizes the table but contains no AutoFit/column-width, wrapping, standardized date format or new-workbook readability policy. Tests verify data mapping and preservation of an existing `0.00` amount format, not column readability. | Separate small formatting assignment after Rob chooses width/wrap/date/currency expectations; preserve export values and existing workbook content. |
| Possible duplicates / maintenance surface | **VERIFIED COMPLETE for existing scope** | The Maintenance UI exposes archived records, duplicate candidates, merge review, email health, backups and diagnostics; the final six-case Form smoke run passed. Existing data tests cover relationship-preserving merge and cross-company rollback. This is not authorization for automatic deduplication. | Stage 2 may rerun only the two safe duplicate data cases to refresh isolated evidence. |
| Smaller UI / Settings appearance notes | **PARTIAL / no single confirmed new defect** | GoGreen Settings at actual 100% is accepted. Existing main-Settings large-text coverage and the prior broad run's one layout assertion do not establish a current product defect; actual 125%/150% is open. Broader Settings regrouping/tab redesign is expressly deferred. | Keep open as manual usability review after functional/package gates; do not redesign now. |

## Broad UI-suite interpretation

The recorded **139 passed / 27 failed / 166 total** run is evidence, not a product PASS and not 27 established product defects.

- Seed-dependent tests in `AcceptanceFeedbackTests`, `CRMWorkbookExporterTests`, `CRMUpgradeTests`, `ContactSaveRegressionTests`, `CRMMaintenanceTests` and deployment-safety coverage reference `AppContext.BaseDirectory\Database\CRM_seed.sqlite`. The operational seed was intentionally excluded, so missing-output-fixture failures are expected environment/fixture failures unless safely rerun with the approved fictional fixture.
- UI timeouts and the one layout assertion remain case-specific environment or presentation evidence, not proven business/data failures. Interactive Stage 3 and November 4 targeted checks supersede the contact menu, Quick Lookup and Excel runtime defects they directly retested.
- The prior `CompanyButtonsCreateEditAndSoftDeleteACompany` null reference was test-side evidence; the later complete `Form1SmokeTests` run passed 6/6. It is not an open product defect.
- No blanket rerun is justified. Stage 2 should run only the selected exporter and duplicate data tests that can be proven offline, non-interactive and fully contained.

## Deferred features and acceptance gaps

The following remain separate and are neither PASS nor authorized implementation: office-only monthly-email/Outlook/Graph testing; successful-send-only Last Interaction/Last Follow-Up timestamp behavior; advanced Quick Lookup delimiters/operators/phrases/grouping; customer-thread acknowledgment; actual GoGreen 125%/150% Windows scaling; and whole-application/Settings regrouping or tab redesign. Package, merge, release and deployment remain unauthorized.

## Stage 2 selection and stop

Stage 2 should statically verify setup and, only if all isolation gates pass, run:

1. The seven data/workbook methods in `CRMWorkbookExporterTests` through `ReorderedContiguousExportTableIsMappedByHeaderAndPreservesOutsideFormula`, excluding the two Form/UI methods and any actual Excel automation.
2. `CRMMaintenanceTests.DuplicateScanAndConfirmedMergeOperationsPreserveRelationships` and `CrossCompanySiteMergeRollsBackWithoutChanges`.

These cases materially clarify export safety/mapping and duplicate integrity without rerunning the already-green 33/33 or Form smoke 6/6. They require a fresh ignored Stage 2 root, a byte-verified copy of the proven fictional schema-24 fixture staged only in the isolated test output, contained `TEMP`/`TMP`, `CRMIncludeOperationalSeed=false`, `--no-restore`, and no network, GUI, Excel process or established artifact modification. Any setup mismatch is BLOCKED/NOT VERIFIED, not permission to broaden access.

**Stage 1 is complete. Proceed only to authorized Stage 2; no source/test edit, fix, package or unrelated work.**
