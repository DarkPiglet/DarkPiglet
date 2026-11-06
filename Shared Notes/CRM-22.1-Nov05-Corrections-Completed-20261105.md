# CRM 22.1 November 5 Corrections — Completion Report

**Date:** November 5, 2026
**Result:** A12 PASS; A02 PASS; A03 PASS; A09 PASS. STOP for Rob/Priya review.
**Authority:** `Shared Notes/CRM-22.1-Nov05-Corrections-Authorized-20261105.md`

## Scope and source integrity

Work was confined to the four authorized corrections, in order, in `C:\Users\Dev\CRM-22.1-Maintenance-20261103` under `desktop-uh85jc0\dev`. The source workspace remained on `codex/crm-22-1-maintenance-20261103`; direct read-only inspection of `.git` established local HEAD and its recorded origin-tracking ref at `a7437f0c3070fa50a0189850e83ea9b6715f54cd`. No Git command was run in that protected workspace.

The recorded twelve tracked modifications and five untracked source/test files that predated this assignment were inventoried before editing and were not reset, discarded, staged, committed, or published. Edits were limited to the eleven source/test paths listed below. Tests used only generated fictional databases and temporary workbooks. No production/workplace database, operational seed contents, backup, recovery file, USB, `Z:`, real mailbox, live Graph call, email send, package, deployment, or application launch was used.

The CRM project handoff was 665,480 bytes before this completion entry and the shared current handoff was 505,631 bytes; both already exceed the 500,000-byte threshold. They are recorded here and were not reorganized. The historical archive scheme and numbered volumes were not changed.

## A12 — Draft-related dates: PASS

**Root cause.** `DraftBatchProcessor` called the CRM follow-up recorder during both newly created draft processing and existing-draft reconciliation. That draft-time path created operational FollowUp/date state before any successful send.

**Correction.** Removed the CRM follow-up recorder dependency and every draft-create/reconciliation call to it. Draft identification, verified-draft audit insertion, duplicate prevention, and resume behavior remain. Main-form status and explanatory text now state that draft creation does not change CRM follow-up/contact dates.

**Verification.** After an initial `--no-restore` attempt was blocked by missing assets (`NETSDK1004`), a cache-only restore using `NuGet.offline.config` succeeded. The focused `DraftBatchProcessorTests` run passed **6/6**, failed 0, skipped 0. It covers create, duplicate/resume, cancellation, verification failure, and simulated Graph failure without an operational follow-up marker. Static inspection found no FollowUp/date recorder call remaining in the processor or main form. A simulated successful-send test is **NOT RUN** because there is no existing verified successful-send boundary; none was invented. The reported workplace crash remains **NOT VERIFIED** and was not treated as fixed.

Canonical evidence: `A12/A12-DraftBatchProcessor.trx`, SHA-256 `A32ABD13F0E5E5D1A5D1D8C600B8368EC958FD25F6D443D46D8F24B0D014333B`.

## A02 — Contact date clearing: PASS

**Root cause.** The nullable picker could change its native checked state without reliably raising the custom binding notification, while programmatic loading could also flow through the standard event path.

**Correction.** `NullableDatePicker` now suppresses custom notifications during programmatic loads; detects mouse checkbox transitions; handles Delete/Backspace; and raises `NullableValueChanged` exactly once for a user change. Site and contact-card binding subscribe only to that custom event.

**Verification.** Component/integration coverage exercises programmatic load suppression, replacement date, keyboard clear, mouse clear, validation, and `RejectChanges` cancel. The disposable synthetic save/reopen route proves Delete clear reaches the bound row, saves SQL `NULL`, and reloads blank with database integrity intact. The initial run and first narrowing retry failed because the test had entered site-edit mode, which intentionally made contact cards read-only; that test-context error was corrected without changing product behavior. Final focused result: **2/2 PASS**, failed 0, skipped 0.

Canonical evidence: `A02/A02-NullableDate-Retry2.trx`, SHA-256 `287ACFE283B9789134A29C521240876DD9C347E99095321C97ACB47ACDA6484B`. Earlier failed evidence is retained as `A02-NullableDate.trx` and `A02-NullableDate-Retry1.trx`.

## A03 — Contact email clearing: PASS

**Root cause.** Blank replacement only removed `IsPrimary`; the row stayed active, and both the repository lookup and reload projection fell back to active non-primary values.

**Correction.** Clearing deactivates only the applicable active primary without deleting it or changing unrelated historical secondary methods. Primary lookup/reload now require active primary rows. Re-entering the same normalized value searches active and inactive history and reactivates the existing row rather than inserting a duplicate. Replacement preserves older active secondary history and all phone methods.

**Verification.** Focused coverage proves clear/save/reload blank, applicable-row deactivation, history preservation, reactivation with stable method ID/count, new replacement, shared-email warning behavior, unchanged phone methods, audit details, cancel lifecycle, and transaction rollback using a fictional aborting audit trigger. The first four-test run passed 3 and failed 1 because reactivation changed the stored display casing. The narrow correction preserved the original stored display value; retry passed **4/4**, failed 0, skipped 0, with database integrity intact and unrelated contacts unchanged.

Canonical evidence: `A03/A03-ContactMethods-Retry1.trx`, SHA-256 `2CA82626CDD5387B29D918FE51F98E5953705C4C5E7223D41D68EDA8482F0070`. The initial 3-pass/1-fail evidence is retained as `A03-ContactMethods.trx`.

## A09 — Excel byte consistency: PASS

**Root cause.** ClosedXML's initial save/resave normalization and variable XLSX ZIP entry ordering/timestamps prevented byte identity even when visible workbook state was identical.

**Correction.** After the bounded workbook update, the working XLSX is canonicalized with ordinal ZIP-entry order, a fixed valid ZIP timestamp, deterministic compression, and preserved entry attributes. ClosedXML resave plus canonicalization repeats only until consecutive package hashes match, with a hard maximum of four resaves; lack of convergence throws before destination replacement. Existing staging and rollback boundaries remain unchanged.

**Verification.** A new test proves exact bytes and SHA-256 match across identical repeated exports for a fresh workbook and a customized existing workbook. It also verifies visible values, formatting, below-table content, and an unrelated sheet. The complete `CRMWorkbookExporterTests` class passed **15/15**, failed 0, skipped 0, covering formulas, tables, styles, reordered headers, unrelated content/sheets, no-data protection, invalid targets, and failure recovery. The dedicated determinism test passed on its first run.

Evidence: `A09/A09-Deterministic-Initial.trx`, SHA-256 `027DB539EE16A2229F5644BB39EC6C9A5679866B1513A47A75AB87E3B2AB8777`; canonical class run `A09/A09-Exporter-Class.trx`, SHA-256 `AB9794A14135BA9C69E545196BC17B20DF1AE43520477BCC409EAFD413A57AFE`.

## Exact source/test files changed

1. `GoGreenMonthlyDrafts/src/GoGreenMonthlyDrafts/DraftBatchProcessor.vb`
2. `GoGreenMonthlyDrafts/src/GoGreenMonthlyDrafts/MainForm.vb`
3. `GoGreenMonthlyDrafts/src/GoGreenMonthlyDrafts/MainForm.Designer.vb`
4. `GoGreenMonthlyDrafts/tests/GoGreenMonthlyDrafts.Tests/DraftBatchProcessorTests.vb`
5. `SiteInformationEditor.vb`
6. `ContactCardsEditor.vb`
7. `Data/CRMRepository.vb`
8. `Data/CRMWorkbookExporter.vb`
9. `tests/CRM.Ui.Tests/ContactCardsEditorTests.cs`
10. `tests/CRM.Ui.Tests/ContactSaveRegressionTests.cs`
11. `tests/CRM.Ui.Tests/CRMWorkbookExporterTests.cs`

Local evidence additionally includes `artifacts/CRM22.1-Nov05-Corrections-20261105/NuGet.offline.config` and the retained TRX files. No other application/source/test path was edited by this assignment.

## Current SHA-256 inventory for changed source/test files

- `DraftBatchProcessor.vb`: `1FE46403F62BBC7D5E281694196C89FAF89CE91CC21FFC69E63F97C1D0DD7C8C`
- GoGreen `MainForm.vb`: `8209D697F797C0CFC1EAF3349B09EBA42130842C35F0AB892A562DC6B6230476`
- GoGreen `MainForm.Designer.vb`: `CC6B6513035F992D6FF40FF35853CEDA4ADF9D95031A39FD26C3E6BFC8D85A86`
- `DraftBatchProcessorTests.vb`: `F114567FC8D3D080A4942C60ADA332FF2DC05E869EEE757745B61E4DDBB4887D`
- `SiteInformationEditor.vb`: `2595A138167C7C00DD8DF13B623E708438A8B2BB86DC9FF6B52035CD13F20DAE`
- `ContactCardsEditor.vb`: `9CDC82F19E1E4AC52BCEF1A2D197DE1D4E83FDD323620B37688257056608DA9D`
- `CRMRepository.vb`: `4232A01ECB3790715922DA13AA0B4EB252709BBD1A3E62E42A82413138D54DE5`
- `CRMWorkbookExporter.vb`: `A2AA25ADB489F7F3EC19123F5D3390220FB771DE51040EE7392D8354D37B7C35`
- `ContactCardsEditorTests.cs`: `3280DA3F57E3CA7F7650A231523C1BBD0F271DC102904BA5269508F51E268930`
- `ContactSaveRegressionTests.cs`: `169CF61A160ACC5D2F8952EF92BA1A5466C2DC73BAEA205E2D3D6F6A295BC88C`
- `CRMWorkbookExporterTests.cs`: `26DBD1B8353847E553861BD1A035B52999273268A695615EA20E6696FC12ACC3`

## Limitations, risks, and recommendation

- No broad suite, standalone production build, interactive application/Excel acceptance, actual workplace-data validation, live Graph/send boundary, package, transfer, deployment, or source publication was run. Those are **NOT RUN**, not PASS.
- A12 removes premature draft-time date/follow-up writes. It does not add successful-send date behavior; that requires a separately verified send boundary and authorization. The reported crash remains unverified.
- A09 is verified against fictional fresh/custom workbooks and the complete existing exporter class. Actual business workbooks and Excel UI remain outside this assignment.
- All corrections remain local, unstaged, uncommitted, and unpushed with the pre-existing accumulated worktree.

**Friday test ZIP recommendation:** do not package or distribute a new ZIP under this assignment. After Rob/Priya review, separately authorize any desired broader regression/interactive acceptance and a fresh candidate package from the reviewed source. No deployment or production correction is implied.

## STOP

The four authorized correction items are complete at focused-test scope. No follow-on phase, packaging, deployment, source Git operation, production-data change, or additional fix is authorized. STOP for Rob/Priya review.
