# CRM 22.1 — Zero-record protection and final maintenance completed

Date: 2026-11-04
Status: **AUTHORIZED STAGES COMPLETE; focused tests 14/14 PASS; isolated Release build PASS; actual warning-dialog interaction NOT VERIFIED; NOT PACKAGE READY; STOP for Rob/Priya review.**

## Authority and preservation

Executed only `CRM-22.1-Zero-Record-Protection-and-Final-Maintenance-Authorized-20261104.md` after Rob's explicit Codex start. Preflight passed as `DESKTOP-UH85JC0\Dev` in `C:\Users\Dev\CRM-22.1-Maintenance-20261103`, branch `codex/crm-22-1-maintenance-20261103`, remote `DarkPiglet/Weekly-Logger-Search-Application`. The source baseline remains `dd223e6f228c236c85b89b1246b587b2a0d1f5c2` / tree `0bfca6c87411c5f8129e35bfde28dc987c954af8`. The complete documented modified/untracked inventory remained present, unstaged and uncommitted.

No source/test commit or push, package, merge, release, deployment, application/Excel launch, live Graph/email/carrier action, production/recovery/USB/`Z:` access, real profile, dependency change or database schema change occurred. Generated output stayed under ignored `artifacts\CRM22.1-ZeroRecordFinal-20261104\Run-01`. Source/test edits remain intentionally unstaged, uncommitted and unpushed; only documentation publication is committed.

## Stage 1 — zero-record no-export protection: PASS

`Data\CRMWorkbookExporter.vb` now queries every selected dataset before opening, creating, staging, clearing or replacing any target. `CRMWorkbookExportNoDataException` identifies every selected empty dataset. Any zero-row selected query blocks the whole request, including both-file requests, while a query/database error remains an ordinary failure. Nonzero single-file behavior and the existing two-file staging/rollback path are retained.

`Form1.vb` removes the former Yes/Continue override. The warning names each empty dataset, says the export did not occur, and says no selected file was created or changed and all selected existing workbooks remain unchanged. It uses only an OK warning and cannot display a zero-row success result. The exporter-side exception is caught separately to protect callers even if data changes between the UI count and export.

Focused tests prove both empty directions, both single-target paths, both combined-target preservation paths, no new workbook creation, byte-for-byte preservation of both existing populated workbook fixtures, no working/backup artifacts, query failure versus valid zero, successful nonzero export, invalid-target rollback, reordered headers, outside formula and custom-width preservation. The actual modal warning was not clicked interactively; its generated text and lack of a Continue override are **PASS by noninteractive component test**, while actual dialog interaction is **NOT VERIFIED**.

## Stage 2 — small export readability correction: PASS

Default formatting applies only when a workbook is newly created. Exported columns receive bounded explicit widths; long-text columns wrap; dates remain typed dates with `mm/dd/yyyy`; Agreement amounts remain numeric with `0.00`. Existing workbooks do not receive the default-formatting pass, preserving custom widths, styles, formulas, unrelated sheets and outside-table content. No column order, table structure, value or dependency changed.

## Stage 3 — Alias presentation correction: COMPONENT PASS

`txtAlias` now uses the neighboring Street Address field's fixed border and remains enabled/readable while read-only for a selected site; edit mode remains enabled and writable. The 100-character limit, value binding, edit/save/cancel/audit path and tab/focus order are unchanged. The focused Form component test verifies border, read-only enabled state, foreground/background parity and edit state. Full interactive visual acceptance was not run.

## Stage 4 — focused verification and integrity: PASS with stated UI limits

Canonical focused result: **14 passed / 0 failed / 0 skipped** for `CRMWorkbookExporterTests`. Key cases are `CombinedExportWithEmptyAgreementLeavesBothExistingWorkbooksByteForByteUnchanged`, `SingleAgreementExportWithNoRecordsCreatesNoWorkbook`, `SingleRcLogExportWithNoRecordsCreatesNoWorkbook`, `CombinedExportWithEmptyRcLogLeavesBothExistingWorkbooksByteForByteUnchanged`, `QueryFailureIsNotReportedAsAnEmptySuccessfulQuery`, `ExportCanCreateOnlyTheConfiguredWorkbook`, `ReorderedContiguousExportTableIsMappedByHeaderAndPreservesOutsideFormula`, `NewAgreementWorkbookUsesReadableDefaultsAndTypedValues`, `NoDataWarningNamesEveryEmptyDatasetAndHasNoContinueOverride` and the Alias component case. The first invocation had 13 pass / 1 test-teardown failure because its intentionally corrupt SQLite file remained locked; the test was narrowed to an unopenable database path, rebuilt, and the complete retry passed 14/14. Canonical TRX: `Run-01\Results\CRMWorkbookExporterTests-Retry.trx`, SHA-256 `201684D07017345D8FD246B4F9E95833C75B11A24772B95863A31C9BE890BB1F`.

Clean isolated offline Release build with `CRMIncludeOperationalSeed=false`: **PASS, 0 warnings / 0 errors**. Final CRM executable SHA-256 is `839FD3A80232753E092E58BEFD7F4F156EE7628658368CF12E1D0AC3F74517C9`; CRM DLL is `FEA6F8FE9ECAB29FEDDBB5D355CBF7FBD72322059B460AD0F21119804D1DAA03`. Final application output contains zero SQLite/seed files.

The approved fictional schema-24 source and isolated test copy remain byte-identical at `0EFDF5FD7BEB5E445CE344D2A5460153E6F3EE0F956A723CC7E330D5837C43A7`; both immutable read-only checks returned `integrity_check=ok` and zero foreign-key rows. The tracked operational seed was hash-checked only and remains `3363942E28E35C3F19E3B502CDB528FF8D2D1051B70025C656EE66420D51E4A9`. Retained Stage 3 DB/seed remain `6EF0DC0155A0C959B50C4591E07BA21E6C3C124D0899C694EDE8A49AB1FF51B9` / `0EFDF5FD...3C43A7`. `git diff --check` passed; index remained empty; the final dirty inventory matches the documented set plus only the four authorized affected paths. No CRM, GoGreen, Excel, testhost or vstest process remained. Run root: 584 files / 424,537,776 bytes, zero reparses, exactly one approved fictional SQLite copy and zero operational-seed hash matches.

Static review found no change to database transactions/audits, UPS/FedEx/Graph behavior, GoGreen suppression windows, credentials, package references or configuration defaults. Existing broad-suite, duplicate-integrity, Form-smoke and order-form evidence was not indiscriminately rerun.

## Decision and STOP

All safely authorized stages are complete. Stage 1 exporter protection, Stage 2 new-workbook formatting and Stage 3 Alias component behavior pass the focused automated route; actual warning-dialog interaction and full-form Alias visual acceptance remain accurately **NOT VERIFIED**. The accumulated worktree remains **NOT PACKAGE READY** because all application/test changes are intentionally uncommitted and no package/merge/release authorization exists. Actual 125%/150% scaling, office email, successful-send timestamp semantics, reporting redesign, management-dependent carrier APIs and AI work remain separate/deferred.

**STOP for Rob/Priya review. Do not begin packaging, maintenance reconciliation or another phase automatically.**
