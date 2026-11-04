# CRM 22.1 — Stage 3 targeted corrections and bounded re-test completed

Date: 2026-11-04
Status: **Three targeted defects PASS; GoGreen 100% PASS, 125%/150% NOT VERIFIED; NOT PACKAGE READY; STOP for Rob/Priya review.**

## Authority and stop boundary

Rob explicitly started only `CRM-22.1-Stage3-Targeted-Corrections-Authorized-20261103.md`. Work ran as `DESKTOP-UH85JC0\Dev` in the existing `C:\Users\Dev\CRM-22.1-Maintenance-20261103` worktree on `codex/crm-22-1-maintenance-20261103`, beginning at documentation HEAD/upstream `b8c2eb9490e37de5bd7277bc69674f740e2d158e`. The expected uncommitted maintenance, Stage 1 and Stage 2 source/test inventory matched the handoffs and was preserved. No reset, clean, checkout, branch switch, merge, source commit or source push occurred.

The separately published post-Stage-3 maintenance reconciliation was not started. There was no schema change, dependency upgrade, refactor, package, release, deployment, production use, real-profile use, USB/`Z:`/recovery access, live Graph/email/carrier action or unrelated phase.

## Isolation and protected-data result

- Reused only the wholly fictional schema-24 fixture in `artifacts\CRM22.1-Stage3-20261103\Run-01`. Runtime database, seed copy, settings, profile/AppData, temp, logs, backups, agreement documents, exports, templates, orders and GoGreen configuration all remained under that isolated root. There were zero reparse points.
- `CRMIncludeOperationalSeed=false` was used for every final test/build. The Release output contained zero `.sqlite` or `CRM_seed` files.
- The isolated seed and protected fixture remained byte-identical at SHA-256 `0EFDF5FD7BEB5E445CE344D2A5460153E6F3EE0F956A723CC7E330D5837C43A7`. The tracked operational seed was not opened, queried, copied, modified, deleted, packaged or used.
- Effective settings used blank carrier credentials, loopback-only carrier URLs, `.example.test` recipients and task-root output/template/backup paths. Microsoft Graph was disabled. A final text scan found no `Z:\`, real stable-profile or prior recovery path in the isolated text configuration/log artifacts.
- Excel 2010 initially could not open a workbook while the isolated `USERPROFILE` lacked standard shell folders. Creating empty `Desktop`, `Documents`, `Downloads`, `Favorites`, `Music`, `Pictures`, `Templates` and `Videos` directories inside the isolated profile resolved that environment-only prerequisite. No real-profile folder was read or written.

## Targeted correction results

### A — Contact cards: PASS

**Reproduction.** The prior Stage 3 run established that blanking an existing contact name and saving silently restored the old value, and that the card Actions popup could extend beyond the right edge.

**Small correction.** `ContactCardsEditor.ValidateRowsOrThrow` now rejects an existing blank name before ending the binding edit, selects the affected card and focuses the name control, then raises the clear message `Contact Name is required.`. `Form1` catches that validation result without reloading the table, so the proposed blank value and editing context are retained. Card Actions now carries its originating button and opens below it with right-to-left placement, allowing WinForms to keep the menu in the visible working area. Existing DataView/BindingSource identity, nonblank rules, add/edit/delete/cancel/save/reload, duplicate-email flow, audit and transaction behavior remain unchanged.

**Interactive re-test.** Blanking existing fictional contact `Jordan Example` and clicking Save displayed a `Validation Error` modal with the exact required message. After dismissal, the same blank field remained visible and focused. Restoring the fictional name and saving succeeded. The Actions menu opened fully on-screen beside the right-edge card with all actions visible. Automated coverage also verifies that the originating Actions button is the popup anchor. Result: **PASS**.

### B — Excel order form: PASS

**Reproduction.** The prior run established that the newly generated staging workbook was not retained/opened by Excel, so no approval/publish path could complete.

**Small correction.** `Form1` now creates an Excel COM instance, opens the exact staged workbook, makes Excel visible and waits until that workbook closes before showing approval. COM references are released after close; if opening fails before a workbook is obtained, the created Excel instance is explicitly quit. Existing staged generation, atomic same-volume replacement/backup, approval/cancel, failure cleanup and activity-write ordering remain intact.

**Interactive re-test.** With the isolated profile prerequisite above, actual Excel opened the newly generated staged workbook with its workbook title and worksheets visible. Email options remained unchecked.

1. New-file approval created `Orders\Northstar Test Foods - Cedar.xlsx`, cleared staging and wrote fictional `BoxOrder` Activity ID 15.
2. A second actual Excel review and approval safely replaced the same destination. The final reviewed file is 45,150 bytes, SHA-256 `65ED722AC8C45BF6AD3E843451E1FFFEAE348B63757D35129C3855F229BE9A21`; staging is empty and Activity ID 16 records the second success.
3. A third review was followed by an exclusive lock on the exact destination. Approval displayed the clear failure that the existing order form could not be replaced and the previous file was retained. The destination length/hash remained exactly 45,150 / `65ED...9A21`, staging returned to zero files, and maximum Activity ID remained 16. No successful activity was recorded for the failed attempt.

Both successful activities are associated with fictional Company 2, Site 2 and Contact 2, and their details point only to the isolated order path. Result: **PASS**.

### C — Quick Lookup on contact cards: PASS

**Reproduction.** The prior run matched and navigated but did not show matched-contact context, exact card highlighting or useful source tooltips.

**Small correction.** Site-result context now identifies contact name, title, email, office phone, mobile phone and contact-note sources with the matched contact label. Each visible matching card control receives the existing subtle green treatment plus an informative tooltip/accessibility description naming its source. The first matching card is selected and scrolled into view. Existing case-insensitive partial matching, company/site hidden-source context and row tooltips remain unchanged; no search grammar was added.

**Interactive re-test.** Typing `Shared@Northstar.Example.Test` expanded the correct fictional company/site result, auto-scrolled `Jordan Example` to the top of the Contact Information area and highlighted the exact email control in green. Automated coverage verifies the exact source tooltip/accessibility description, second-card selection/scroll behavior and matched-contact context for all supported contact sources. Result: **PASS**.

## GoGreen DPI/layout result

The host reported 96 DPI, i.e. actual Windows scaling **100%**. At 100%, the isolated GoGreen Settings window was inspected restored, and the main window was inspected restored, narrowed to approximately 1066×749, and maximized to approximately 2560×1416. The complete manual-override checkbox label, month selector, action button, readiness text, activity/status area and Settings fields/tabs/spinners/buttons were visible without overlap or clipping. Result at 100%: **PASS**.

Actual **125%** and **150%** are **NOT VERIFIED**. Changing the host-wide Windows display scale is a system-setting action that requires action-time confirmation and can disrupt the shared desktop session; it was therefore not silently changed under the authorization's “only if safely permitted” condition. No GoGreen defect was reproduced at 100%, and no new GoGreen source change was made in this assignment.

Exact remaining manual procedure:

1. Record the original Windows scale. In Settings > System > Display, set Scale to 125%; sign out/in only if Windows requires it.
2. Launch CRM with the same isolated `Run-01` database, settings, profile/temp/log and Graph-disabled environment; open Monthly Drafts.
3. Inspect GoGreen Main restored, a deliberately narrow resize, and maximized. Confirm the complete manual-override checkbox label, month selector, Create Email Drafts control, readiness/activity/status areas and scroll behavior do not overlap or clip.
4. Open Tools > Settings and inspect every tab restored and narrow; confirm the adjacent folder/selector fields, spinners, checkbox labels, Save/Cancel and status text remain fully visible.
5. Repeat steps 1–4 at 150%, then restore the original 100% scale and confirm it took effect.

## Automated, database and build evidence

- Directly affected plus prior focused baseline: **33/33 passed**, 0 failed/skipped. Command: `dotnet test tests\CRM.Ui.Tests\CRM.Ui.Tests.csproj --configuration Release --no-restore -p:CRMIncludeOperationalSeed=false --filter "FullyQualifiedName~ContactCardsEditorTests|FullyQualifiedName~SiteInformationEditorTests|FullyQualifiedName~MaintenanceRegressionTests|FullyQualifiedName~ExcelOrderFormGeneratorTests"`.
- Narrowly relevant form smoke: **6/6 passed**, 0 failed/skipped. This also clears the prior test-side company-button null-reference result.
- Final offline Release build: **PASS**, 0 warnings / 0 errors. `CRM.exe` SHA-256 `1DA7B9D2E0DDCBE0F8C5B3DED7AA60E12B49AD0CE141A25775F12F6F5E675232`; `CRM.dll` SHA-256 `D474691A7DB046C3D86BF4D218FBFB051F677B65AE30A30FA648112691137038`.
- `git diff --check`: **PASS**. The earlier broad suite was not repeated because its documented 27 failures are dominated by missing operational-seed fixtures, timeouts and one prior helper failure; the authorization required the focused baseline and narrow relevant checks, not a misleading blanket rerun.
- Final fictional database SHA-256 `6EF0DC0155A0C959B50C4591E07BA21E6C3C124D0899C694EDE8A49AB1FF51B9`; the expected change from pre-correction `8FDCC840...697086` is limited to the two successful fictional BoxOrder audits and their existing interaction-date behavior. SQLite `integrity_check` is `ok`; `foreign_key_check` returns zero rows; maximum Activity ID is 16.
- Final order staging contains zero files. No CRM, GoGreen, Excel or test-host process remained.

## Exact targeted paths and stop

This assignment made targeted source/test edits only within:

- `ContactCardsEditor.vb`
- `Form1.vb`
- `tests/CRM.Ui.Tests/ContactCardsEditorTests.cs`
- `tests/CRM.Ui.Tests/MaintenanceRegressionTests.cs`

All of those files already belonged to the preserved uncommitted Stage 1/Stage 2/maintenance working tree. The complete pre-existing dirty inventory remains unstaged, uncommitted and unpushed. Only this report and the two required handoffs may be committed and pushed.

The three authorized defect groups are corrected and verified. GoGreen 100% is verified; 125% and 150% remain accurately NOT VERIFIED pending the manual procedure above. The accumulated source is therefore **NOT PACKAGE READY**, and packaging/merging/release remains unauthorized. **STOP for Rob/Priya review. Do not begin maintenance reconciliation or any subsequent phase.**
