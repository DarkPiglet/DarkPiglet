# CRM 22.1 — November 5 consolidated investigation

Date: 2026-11-05  
Status: INVESTIGATION COMPLETE; NO PRODUCT FIX, PACKAGE, OR DEPLOYMENT; STOP FOR ROB/PRIYA REVIEW

## Authority and environment

Executed only `CRM-22.1-Nov05-Consolidated-Investigation-Authorized-20261105.md`. The verified isolated source workspace is `C:\Users\Dev\CRM-22.1-Maintenance-20261103` on `codex/crm-22-1-maintenance-20261103`. Direct ref-file inspection (no Git command) found local/recorded remote branch SHA `a7437f0c3070fa50a0189850e83ea9b6715f54cd`. The November 4 candidate remains the build from source commit `1b17a5cdbbe00b7bcb5816343d0fd8f36f0a5977` plus tracked dirty-diff SHA-256 `44C77B0A4F047B196FBE7CE86AAE0D8CD62FD3FD5A1813B66DAC1BE62D68A8FE`; all five recorded untracked source/test hashes still match.

Candidate identities rechecked: `CRM.exe` `3C4F9E861498E9643EE1173AC429F0CE3CD94AE2D3CA3F619CE6674C9B950C68`; `CRM.dll` `85A1E3AA6E557467DD0958AFC11BB914D7CC2F7BAA5DEFAF2630556E61C7C627`; `GoGreenMonthlyDrafts.dll` `3638DCA73DF0807C72102ADE2328F63BEB95AB88C09FF83CFDA9D9840B8AC579`. Relevant dependencies are .NET `net10.0-windows`, ClosedXML `0.105.0`, and Microsoft.Data.Sqlite `10.0.9`. Prior baseline remains exporter 14/14 PASS, seed-disabled Release build 0 warnings/errors, and interactive 2/2 PASS at 96 DPI only; those results were not rerun or broadened.

## Results

### A12 Step 4 — FAIL for date semantics; crash and workplace rows NOT VERIFIED

**Confirmed cause of the apparent date changes.** `DraftBatchProcessor.ProcessAsync` records a CRM follow-up immediately after a Graph draft is created and verified, and also repairs that follow-up when an existing draft is found (`DraftBatchProcessor.vb:76-89,120-138`). `CrmFollowUpRecorder.EnsureRecorded` then atomically inserts a `FollowUp` Activity, updates matching recipient contacts' `SiteContact.LastInteractionDate`, and inserts `MonthlyDraftFollowUp` (`CrmFollowUpRecorder.vb:64-95,108-145`). CRM derives site Last Follow-Up from the latest non-superseded `FollowUp` Activity. The UI even states that draft creation “records today's Last Follow Up” (`MainForm.vb:305-309`). This violates the November 5 rule that draft creation, attempted send, and failed send must not update those fields; only confirmed successful actual send may do so.

Disposable fictional reproduction against a copy of fixture SHA-256 `0EFDF5FD7BEB5E445CE344D2A5460153E6F3EE0F956A723CC7E330D5837C43A7` used Site 2 / Contact 2 and a synthetic draft ID. Before: FollowUp Activity count `0`, LastInteractionDate `NULL`, MonthlyDraftFollowUp count `0`. Calling the candidate recorder once produced count `1`, LastInteractionDate `2026-11-05`, ledger count `1`, and Activity summary `Monthly GoGreen draft created`. The original fixture hash remained exact. This makes Rob's observation of one or two changed sites technically consistent with the number of drafts created, but the actual workplace database was not accessed and its mutations remain NOT VERIFIED.

**Crash/disappearance:** NOT VERIFIED. The Dev VM has no November 5 CRM/GoGreen app log; its newest GoGreen log is November 4 and contains only two prior start/normal-close pairs. Windows Application event access is denied in this execution context, and these are not the work-machine events. Managed exceptions in the draft workflow are caught and shown; CRM launches Monthly Drafts as an owned modal dialog and intentionally disables the owner while it is open (`Form1.vb:1168-1193`). Modality can explain ignored clicks on the CRM owner, but not an unexplained process disappearance. No crash cause is claimed.

**Smallest proposed fix:** remove CRM follow-up/contact-date recording from the draft-only processor and its reconciliation path; retain draft audit/idempotency only. Add any future date update only after a separately defined Graph send-success confirmation. Update the misleading UI/status text. Do not rewrite existing operational dates without separate record-level evidence and authorization.

**Required tests:** draft create, duplicate/resume, verification failure, Graph failure, and cancellation must leave Activity, MonthlyDraftFollowUp, and SiteContact dates unchanged; simulated confirmed send may update exactly the intended site/recipient once; failed/unknown send must not. Replace current tests that explicitly expect draft-time follow-up creation.

### A02 Step 5 — FAIL; UI clear does not reach persistence

The first contact date field is `ContactInteractionDate` / **Last Interaction**. `NullableDatePicker` returns blank when unchecked, but setting `Checked=False` raises neither `ValueChanged` nor the custom `NullableValueChanged`. `ContactCard` updates the bound row only from those two events (`ContactCardsEditor.vb:443-444,492-501`). Therefore the control appears blank while the DataRow retains the old text; Save sees no date change and reload restores the old date. Entering a new date changes `Value`, fires the subscribed event, and persists, matching the workplace report.

Exact component probe: bound value began `11/01/2026`; after uncheck the picker text was blank but the bound row remained `11/01/2026`; entering `11/03/2026` changed the row to `11/03/2026`. The repository path itself is correct: on a disposable DB, setting `2026-11-01` and then explicitly passing `Nothing` reloaded as SQL `NULL` (`CRMRepository.vb:1042-1052`; `Form1.vb:1819-1822`). Workplace stored values were not inspected, so their before/after state is NOT VERIFIED; the code path predicts no database change from the failed clear.

**Smallest proposed fix:** make every user check-state transition, including Delete/Backspace and mouse checkbox clear, raise one nullable-value change event without firing during programmatic load. Add a card-level Save/reload regression for keyboard clear and mouse clear, plus existing new-date behavior and cancel.

### A03 Step 2 — FAIL; blank email remains active and reloadable

`ReplacePrimaryMethod` handles blank values by setting `IsPrimary=0` only; it leaves matching `ContactMethod` rows active (`CRMRepository.vb:1650-1657`). Both `PrimaryMethod` and `CRMContactView` select any active method, merely ordering primary first (`CRMRepository.vb:1596-1600`; `Database/CRM_v13.sql:44-46`). The demoted email therefore remains the only active candidate and reappears on reload.

Disposable reproduction used fictional Contact 2 / Site 2 (`Jordan Example`). Before email: `Shared@Northstar.Example.Test`. After calling the candidate `UpdateContact` with blank email, `LoadContacts` returned the same email. Direct inspection showed ContactMethod ID 3 with the old value, `IsPrimary=0`, `IsActive=1`.

**Smallest proposed fix:** blanking a method must deactivate it as well as clear primary state. Re-entering the same normalized value must reactivate the existing unique row rather than attempt a duplicate insert; selecting/displaying a primary method should not silently fall back to a non-primary active method when the UI contract is one editable value. Cover clear/save/reload, clear/cancel, re-entry of the same value, replacement with a new value, shared-email warnings, phones, audit text, and transaction rollback.

### A09 Test 2 — FAIL for byte identity; workbook semantics match

The original four workplace XLSX files were unavailable, so no claim is made about their exact package deltas. A safe isolated RCLog reproduction used the unchanged fictional fixture and candidate exporter. Three generations from the same rows were retained:

- generation 1: 8,495 bytes, SHA-256 `38DF942310205034CC68ED93557EE0FEAD17E7B131CA354BA04294D5F956A551`
- generation 2: 8,500 bytes, SHA-256 `9A938C0A4C32E0C259E2CD1DDEA4A1B46A924855801137D269ECEB7AD5C5F1B5`
- generation 3: 8,500 bytes, SHA-256 `3B930FA87573ABF6397FD9FB02626DE9380B536906F440FA878B7B92CA8E25F8`

All three contain 75 used cells, the same `A1:AB3` table, and zero visible-value or formula differences. Generation 1 to 2 changed `xl/sharedStrings.xml` and `xl/worksheets/sheet1.xml`, consistent with first-save normalization. Generation 2 to 3 had **zero decompressed entry-content differences**; only the ZIP timestamp for `[Content_Types].xml` changed, which alone changes the whole-file SHA-256. ClosedXML save therefore cannot satisfy repeated byte identity as currently used even when workbook semantics are identical. The acceptance criterion is not relaxed.

**Smallest proposed fix:** make the first and later save paths produce the same XML model, then canonicalize the final XLSX package with deterministic entry ordering, compression, and fixed timestamps before replacement. Tests must export identical fictional data into a new workbook and repeatedly update the same workbook, preserve both generations, require identical SHA-256, and also recheck visible cells, formulas, tables, styles, unrelated sheets/content, and rollback behavior.

### A08 and other results

A08 display scaling was NOT RUN, as required. A01, A04-A06, A10-A11 and the reported History search result remain prior PASS evidence only. A07 and A13 remain NOT RUN; no email was sent. The intermittent stuck-label report was not investigated speculatively. Deferred layout suggestions remain backlog.

## Priority for a separately authorized Friday correction

1. Fix A12 first because current draft-only behavior writes operational Activity/contact dates by design; add no-write-on-draft tests before any other runtime exercise.
2. Fix A02 and A03 as narrow independent contact persistence defects; add exact clear/save/reload and reactivation tests.
3. Implement deterministic XLSX serialization for A09 without weakening byte-identity acceptance.
4. Obtain work-machine crash logs/events and a protected read-only record snapshot only under separate authorization; do not infer or repair workplace rows from this investigation.
5. Keep A08 as a separate interactive scaling assignment.

## Containment and stop

Only disposable copies under `artifacts\CRM22.1-Nov05-Investigation-20261105\Run-03` through `Run-05` were changed. The original fictional fixture remained exact at `0EFDF5FD7BEB5E445CE344D2A5460153E6F3EE0F956A723CC7E330D5837C43A7`. No CRM/GoGreen/Excel process remained. No product source/test file, authoritative database, backup, USB, Z: operational copy, recovery, real mailbox, Graph endpoint, display scaling, package, or deployment was changed or used. No product build or existing test suite was run; the evidence comes from static inspection and bounded reflection/SQLite/ClosedXML probes against the already-built candidate and disposable fictional data.

**STOP for Rob/Priya review. Investigation does not authorize fixes, source publication, packaging, or deployment.**
