# CRM 22.1 — Exporter regression follow-up completed

Date: 2026-11-04  
Status: **COMPLETE within the approved boundary; zero-row correction BLOCKED by ClosedXML 0.105 feasibility; targeted results 3 PASS / 2 FAIL; STOP for Rob/Priya review.**

## Authority and preflight

Executed only `CRM-22.1-Exporter-Regression-Next-Assignment-20261104.md` after Rob's normal start instruction. Preflight passed as `DESKTOP-UH85JC0\Dev` in the existing `C:\Users\Dev\CRM-22.1-Maintenance-20261103` workspace on `codex/crm-22-1-maintenance-20261103`, remote `DarkPiglet/Weekly-Logger-Search-Application`. Source baseline remains commit `dd223e6f228c236c85b89b1246b587b2a0d1f5c2`, tree `0bfca6c87411c5f8129e35bfde28dc987c954af8`. The complete pre-existing modified/untracked application/test inventory matched before and after.

No application or test source was changed, staged, committed or pushed. No application, GUI, Excel automation, live service, production/operational/customer/recovery data, real settings/profile, USB, `Z:`, package, merge or deployment was used. Generated probes, copied fictional fixtures, test binaries, profile/temp files and results were confined to the ignored root `artifacts\CRM22.1-ExporterRegression-20261104\Run-01`.

## 1 — Zero-record Agreement table feasibility: BLOCKED; no correction made

The requirement was tested directly with the exact shipped `ClosedXML 0.105.0` assembly:

1. Creating a table from a header-only `A1:B1` range returned `A1:B2`; `DataRange` was non-null with one row after save/reload.
2. A probe workbook's raw OOXML table reference and auto-filter were changed from `A1:B2` to `A1:B1`. Reloading that file through ClosedXML again exposed `A1:B2`, a non-null data range and one data row.

Therefore the required observable state — a visible header row and zero data rows in the table, with the affected tests inspecting `IXLTable.RangeAddress` through ClosedXML — is not representable in the current library. ClosedXML enforces/normalizes the table to at least one data row even when the underlying OOXML reference is patched. Per the explicit instruction, tests were not weakened to accept an unwanted blank row and no exporter or other source correction was attempted.

Smallest future decision, requiring separate authorization, is whether to change the required workbook representation or evaluate a different/updated Excel writer that can create and round-trip the required structure. This run does not approve either choice.

## 2 — Minimum fictional Agreement precondition: COMPLETE

Two independent copies of the already isolated UI test binaries were made. The zero-row copy retained the approved fictional schema-24 seed unchanged at SHA-256 `0EFDF5FD7BEB5E445CE344D2A5460153E6F3EE0F956A723CC7E330D5837C43A7`. Only the second disposable seed copy received one minimum fictional active Agreement export row through existing repository APIs:

- company `Exporter Fixture Company`, customer `EXP-FIX-001`;
- item `EXP-ITEM-001`, description `Fictional recyclable sensor`, type `Fixture`;
- amount `12.50`, payment type `Payment`.

The resulting disposable seed hash is `F83184DE9394B4C9894F36214747C6B21EB0E66C19847EFE07FCDD1394572EDE`; `integrity_check=ok`, zero foreign-key rows and exactly one Agreement export row. The approved source fixture stayed unchanged at `0EFDF5FD...3C43A7`.

## 3 — Three affected exporter cases

Only the three authorized cases ran, split so the first two used the unchanged zero-Agreement fictional seed and the third used the one-Agreement disposable copy.

- **FAIL** — `ExportCreatesBothWorkbooksWhenConfiguredFilesDoNotExist`: expected last table row 1; actual 2. This is the confirmed ClosedXML minimum-one-data-row behavior.
- **FAIL** — `ExportReplacesOnlyTargetTableRowsAndIncludesOnlyActiveRecords`: expected last table row 3; actual 4. Same feasibility blocker.
- **PASS** — `ReorderedContiguousExportTableIsMappedByHeaderAndPreservesOutsideFormula`: the minimum fictional Agreement satisfied the missing precondition; header mapping and the outside formula were preserved.

Exporter result: **1 PASS / 2 FAIL / 3 total**. Evidence:

- `Zero\Results\ZeroRows.trx`, SHA-256 `0E86FA6D2CE947C7DBC7C59399C79BD413CAADD455D5FA349DBF799CBF46F026`;
- `Agreement\Results\ReorderedAgreement.trx`, SHA-256 `5F7BAADF7A602E649D9BFCA71FC7CDAE0D88EB05AD63DD00001F992BD12C7363`.

## 4 — Previously blocked duplicate-integrity cases: PASS

A narrowly scoped offline restore/build of only `tests\CRM.Data.Tests\CRM.Data.Tests.vbproj` used already cached packages, a run-owned NuGet configuration with package and audit sources cleared, `CRMIncludeOperationalSeed=false`, and run-owned intermediate/output directories. Build result: **PASS, 0 warnings / 0 errors**. The approved fictional fixture was then copied only into that isolated test output.

- **PASS** — `DuplicateScanAndConfirmedMergeOperationsPreserveRelationships`.
- **PASS** — `CrossCompanySiteMergeRollsBackWithoutChanges`.

Data result: **2 PASS / 0 FAIL / 2 total**. Evidence: `DataRun\Results\DuplicateIntegrity.trx`, SHA-256 `F81B025E23F377683049632253813DD89A9665D92BB445E4230B69A5A032BD82`.

## 5 — Final isolation and preservation checks

- Run root: 597 files / 270,941,383 bytes; zero reparse points.
- Exactly three SQLite files: unchanged fictional copies in the zero-row and Data-test outputs plus the intentionally modified one-Agreement disposable copy. Zero files match the operational-seed hash.
- All three SQLite copies: `integrity_check=ok`, zero foreign-key rows.
- Protected tracked operational seed unchanged: `3363942E28E35C3F19E3B502CDB528FF8D2D1051B70025C656EE66420D51E4A9`.
- Approved fictional source and retained Stage 3 seed unchanged: `0EFDF5FD...3C43A7`.
- Retained Stage 3 database unchanged: `6EF0DC0155A0C959B50C4591E07BA21E6C3C124D0899C694EDE8A49AB1FF51B9`.
- No CRM, GoGreen, Excel, testhost or vstest process remained.
- `git diff --check` passed; `Data\CRMWorkbookExporter.vb` has no diff; the source/test dirty inventory is exactly the preflight inventory.

The first zero-row test invocation used a malformed results-directory argument and started no tests; it created only .NET first-run material, including a development certificate, inside the isolated profile. The corrected invocation produced the evidence above. The other fresh isolated profiles likewise kept their .NET first-run files inside the run root.

## Decision and STOP

Combined targeted result: **3 PASS / 2 FAIL / 5 total**. The missing Agreement precondition and both duplicate-integrity gaps are resolved. The two zero-row exporter failures remain open because the mandated table structure is infeasible under the current ClosedXML version, not because a permitted smallest correction was omitted. The accumulated worktree remains **NOT PACKAGE READY**, and the separate future tasks listed in the authorization remain unapproved here.

**STOP for Rob/Priya review. Do not change the tests, select a replacement writer/library, implement formatting or Alias/UI work, perform DPI/email tests, commit source, package, merge or deploy without a new explicit assignment.**
