# CRM 22.1 — Test-candidate packaging completed
Date: 2026-11-04
Status: PASS — NONPRODUCTION TEST CANDIDATE CREATED AND VERIFIED; NOT DELIVERED; STOP FOR ROB/PRIYA REVIEW

## Result

Executed only the explicitly started conditional test-candidate packaging assignment. Gate 1 passed, so Gate 2 produced one clearly labeled, self-contained Windows x64 archive from the actual accumulated uncommitted CRM 22.1 working source. The candidate is for Rob's November 5 workplace testing only. It is not a production release, has not been transferred to Rob, and does not establish workplace, 125%/150% DPI, live-email, or production acceptance.

## Gate 1 — readiness PASS

- Verified `DESKTOP-UH85JC0\Dev`, workspace `C:\Users\Dev\CRM-22.1-Maintenance-20261103`, branch `codex/crm-22-1-maintenance-20261103`, project HEAD/upstream `1b17a5cdbbe00b7bcb5816343d0fd8f36f0a5977`, and original source baseline/merge-base `dd223e6f228c236c85b89b1246b587b2a0d1f5c2`. The index was empty and `git diff --check` passed.
- Read-only source inspection confirmed the combined zero-record export guard queries all selected datasets before target access, blocks the full request on any empty selection, and presents an OK-only no-export/no-file-change message; the bounded new-workbook readability formatting and existing-workbook preservation logic are present; Alias has the same fixed border as Street Address and retains its existing binding/edit/save/cancel behavior.
- Reconciled the recorded final focused exporter result (**14/14 PASS**), isolated Release build (**0 warnings / 0 errors**, operational seed disabled, zero output SQLite database files), and actual interactive verification (**2/2 PASS at 96 DPI / 100% only**). Source timestamps and the unchanged inventory confirm the recorded final build followed the last source/test edit. These are not a broad-suite PASS, 125%/150% acceptance, or Rob's workplace acceptance.
- The established clean Release packaging method is a self-contained `win-x64` publish followed by removal of the complete `Database` schema folder and symbol files. Operational-seed-dependent packaging scripts were intentionally not used.

## Source identity and preserved dirty inventory

The package was built from project HEAD `1b17a5cdbbe00b7bcb5816343d0fd8f36f0a5977` plus the verified working-tree changes. The UTF-8 tracked binary-diff SHA-256 before and after packaging is `44C77B0A4F047B196FBE7CE86AAE0D8CD62FD3FD5A1813B66DAC1BE62D68A8FE`.

Tracked modified paths remained exactly:

- `CRM.vbproj`
- `Data/CRMWorkbookExporter.vb`
- `ExcelOrderFormGenerator.vb`
- `FedExCompletionDialogs.vb`
- `Form1.Designer.vb`
- `Form1.vb`
- `GoGreenMonthlyDrafts/src/GoGreenMonthlyDrafts/MainForm.Designer.vb`
- `tests/CRM.Data.Tests/CRM.Data.Tests.vbproj`
- `tests/CRM.Ui.Tests/AcceptanceFeedbackTests.cs`
- `tests/CRM.Ui.Tests/CRMWorkbookExporterTests.cs`
- `tests/CRM.Ui.Tests/ExcelOrderFormGeneratorTests.cs`
- `tests/CRM.Ui.Tests/Form1SmokeTests.cs`

Untracked source/test identity remained:

- `ContactCardsEditor.vb` — 22,545 bytes — `CDFCEAD16D4B56EE2EDC12F8002FAAABC59B6074494E791FF27D448289CDDFA1`
- `SiteInformationEditor.vb` — 9,851 bytes — `BF1F1C34CC9F27C6F8DF9891A7CE32C874E78F41EA222FAE032BB34E7A649645`
- `tests/CRM.Ui.Tests/ContactCardsEditorTests.cs` — 12,628 bytes — `C0DB56E75309A1F3FB9C425AF25EECA10ACA9E5B915996675DDF602E6BC78427`
- `tests/CRM.Ui.Tests/MaintenanceRegressionTests.cs` — 3,325 bytes — `C68818BFFD5C9E44FAEF0A93BD5AD20172C0F1B12961F6CC06F8907AC24D685F`
- `tests/CRM.Ui.Tests/SiteInformationEditorTests.cs` — 5,727 bytes — `8BC25B8D0713A6F0B0FE4A352ADE78A667DA87E9E5DBD21C94A42969EF423EEF`

No application or test source was reset, cleaned, staged, committed, pushed, merged, or rebased.

## Build and package

- Isolated run root: `C:\Users\Dev\CRM-22.1-Maintenance-20261103\artifacts\CRM22.1-TestCandidate-20261104\Run-01`
- Restore: `dotnet restore CRM.vbproj --runtime win-x64 -p:CRMIncludeOperationalSeed=false`
- Publish: `dotnet publish CRM.vbproj --configuration Release --runtime win-x64 --self-contained true --no-restore --output <Run-01\RawPublish> -p:CRMIncludeOperationalSeed=false -p:Version=10.0.0-test.22 -p:FileVersion=10.0.0.22 -p:SourceRevisionId=1b17a5cdbbe00b7bcb5816343d0fd8f36f0a5977-dirty-44c77b0a`
- The first publish invocation was prevented by the session filesystem sandbox before compilation. The identical authorized command was rerun with access to the preserved workspace and passed with **0 warnings / 0 errors**. No source correction was required.
- Package directory: `Run-01\CRM-22.1-TEST-CANDIDATE-win-x64-20261104-NOT-FOR-PRODUCTION`
- Archive: `Run-01\CRM-22.1-TEST-CANDIDATE-win-x64-20261104-NOT-FOR-PRODUCTION.zip`
- Archive size: 56,534,127 bytes
- Archive SHA-256: `DC24A04897F8FEC00C8A990D6A8BF9546AEF6B8BB5A9B6AE5B43B6D0595E5A54`

## Package verification PASS

- The package and clean extraction each contain 290 files / 138,022,178 bytes. Every relative path, length, and SHA-256 matched after extraction; mismatch count is zero. Canonical sorted tree SHA-256 is `76BD94DFD5B320F80E1F1B8FF8118364A8B78AC499AEDFD1D3927F6DF7CF9B6C`.
- ZIP inspection found 290 entries, all below the single labeled root, with zero absolute, parent-traversal, or wrong-root entries. The package has zero reparse points.
- Required CRM and GoGreen executables, DLLs, `.deps.json`, `.runtimeconfig.json`, `Blank Order Form.xlsx`, and self-contained runtime files (`coreclr.dll`, `hostfxr.dll`, `hostpolicy.dll`) are present. Both executables report PE machine `0x8664` (AMD64), file version `10.0.0.22`, and product version `10.0.0-test.22+1b17a5cdbbe00b7bcb5816343d0fd8f36f0a5977-dirty-44c77b0a`.
- `CRM.exe` SHA-256: `3C4F9E861498E9643EE1173AC429F0CE3CD94AE2D3CA3F619CE6674C9B950C68`
- `CRM.dll` SHA-256: `85A1E3AA6E557467DD0958AFC11BB914D7CC2F7BAA5DEFAF2630556E61C7C627`
- `GoGreenMonthlyDrafts.exe` SHA-256: `888A4460D9017B71E6808F7FBA466DB54F4C2C00434C264400400A4910ED1FEA`
- Content inspection found zero `Data`/`Database` trees, SQLite database/sidecar files, operational seed, settings/profile files, credentials/tokens, recovery/backup artifacts, logs, PDBs, or nested archives. Text metadata contained zero local-user/repository path leaks. SQLite runtime libraries remain because they are required application dependencies; no SQLite database is included.
- Final workspace postflight matched the preflight inventory and tracked-diff identity, the index remained empty, `git diff --check` passed, and no CRM, GoGreen, or Excel process remained.

## Limits and STOP

No package smoke launch was needed: the candidate was freshly compiled from the verified source, the same functional source had the recorded focused and interactive evidence above, and the archive/extraction comparison is exact. No live Microsoft Graph, email, carrier, customer, production, USB, `Z:`, recovery, or operational database action occurred. No package was installed, deployed, emailed, uploaded, or delivered.

**PASS for local nonproduction test-candidate creation and archive verification only. STOP for Rob/Priya review and Rob's workplace acceptance. Do not begin maintenance reconciliation, production release, merge, deployment, or any later phase without separate explicit authorization.**
