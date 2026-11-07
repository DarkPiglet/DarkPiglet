# CRM 22.1 / GoGreen read-only cleanup inventory — November 7, 2026

## Authority and limits

Executed only `CRM-22.1-Cleanup-Inventory-ReadOnly-Authorized-20261107.md` under verified non-elevated `DESKTOP-UH85JC0\Dev`. This report is an inventory and future disposition proposal, not cleanup authorization. No file, branch, workspace, artifact, archive, database, package or handoff was deleted, moved, renamed, pruned, reset or otherwise cleaned. No application source, build, test, release or deployment action occurred.

Discovery was restricted to the CRM/GoGreen GitHub repository, the current CRM and shared documentation repositories, the known CRM/GoGreen paths under `C:\Users\Dev\source\repos`, the documented protected maintenance checkout, and the current Codex visualization task root. No user-profile-wide search, external drive, USB, `Z:`, recovery, customer or production location was traversed. No SQLite file was opened, hashed, copied or queried. Workspace sizes below exclude `.sqlite` files.

## Confirmed current authority and source map

| Role | Confirmed location/ref | Evidence | Disposition |
|---|---|---|---|
| Canonical source repository/default branch | `DarkPiglet/Weekly-Logger-Search-Application:master` | Live head `2ed9bf00b94cf4c97967abc871d60eac9869f92e`; GitHub reports `master` as default. Changes after source merge `0aa39d212d5a6e1f387b4444b2dcab60855462d0` are only `HANDOFF.md`. | KEEP |
| Last verified source milestone | Merge `0aa39d212d5a6e1f387b4444b2dcab60855462d0`; test source `7d959edcdd63830b88c244668a37977b6498fcc3` | `master` contains both and the published UI-test file remains at its verified content. | KEEP |
| Project current handoff | `DarkPiglet/Weekly-Logger-Search-Application:master/HANDOFF.md` | Live branch and fresh sparse checkout verified. | KEEP |
| Shared current handoff | `DarkPiglet/DarkPiglet:main/Shared Notes/Handoff.md` | Live head before this report `494a96593da556146e6ed06d320234fcf77d8ddb`; fresh sparse checkout verified. | KEEP |
| Historical handoff index/volumes | `DarkPiglet/DarkPiglet:main/Shared Notes/Handoff-history.md` and numbered volumes | Explicitly protected historical evidence; not needed for this inventory and not opened or changed. | KEEP |
| Next UI development branch | Not yet authorized or unambiguously identified | Existing branch names are historical. `master` is a canonical base, not automatic authority to choose a new working branch. | UNKNOWN — Rob must choose/authorize |

The protected daily project checkout at `C:\Users\Dev\source\repos\Weekly-Logger-Search-Application` is **not** a safe next-UI-work base: it is on `codex/crm-option-a-p1-20261029` at local `295845912f5a4fefe56464b490dffd5ab502e7a3`, 43 commits behind that remote branch, with 326 staged and two unstaged paths. Future UI work should begin only from a newly verified isolated checkout of the then-current authorized ref.

## Remote branch inventory

GitHub reported 29 branches, no open pull requests, and no protected branches. Repository setting `delete_branch_on_merge=false` explains retained merged refs. Three pull requests exist and are closed/merged: #1 `codex/box-order-workflow`, #2 deleted head `codex/company-grid-accordion`, and #3 `codex/integrate-monthly-drafts-maintenance`.

### Keep or review before any branch removal

Counts are `master-only / branch-only` commits from the live graph; unique paths are changes from the merge base.

| Branch | Tip | Counts | Unique paths | Evidence/risk | Proposal |
|---|---|---:|---:|---|---|
| `master` | `2ed9bf00b94cf4c97967abc871d60eac9869f92e` | 0 / 0 | 0 | Default and canonical source/documentation branch. | KEEP |
| `codex/crm-22-1-maintenance-20261103` | `de53aa966ee994f23f65adc4d4df9d15c8e35e64` | 7 / 14 | 1 | Fourteen unique November 7 documentation commits; application source was integrated, but branch-only handoff evidence remains. | REVIEW FOR ARCHIVE |
| `codex/crm-audit-ledger-20261027` | `1228cf3e840156b5a1607967a1dc20f044986b7d` | 70 / 17 | 20 | Unique WIP/audit-ledger history and source paths. | KEEP / UNKNOWN |
| `codex/crm-contact-save-fix` | `d502271dd66fa5b0a9491c7ec67e54b51cdbd0c6` | 221 / 1 | 4 | One unique source commit; patch equivalence to later work not established. | KEEP / UNKNOWN |
| `codex/crm-contact-save-focused-follow-up` | `149b4a7d7513ac11bf26780c9ef0f3b97b58cd12` | 221 / 2 | 4 | Two unique source commits; patch equivalence not established. | KEEP / UNKNOWN |
| `codex/crm-option-a-p1-20261029` | `e2f33d7aa7b0c546fbf0641aab86ab5961c23e19` | 70 / 56 | 24 | Large unique Option A/P1/P2/P3 history; protected local checkout is dirty on an older ancestor. | KEEP |
| `codex/crm-test22-contact-save-synthetic-package-20261021` | `5d250890226cc1560158e57f5836cfde7f5df47e` | 205 / 1 | 1 | One branch-only documentation/package-validation commit. | REVIEW FOR ARCHIVE |
| `codex/test22-manual-findings-20261026` | `07e779f161671d509ef60622072605f461aa2af7` | 70 / 7 | 1 | Seven branch-only documentation commits. | REVIEW FOR ARCHIVE |

### Fully merged remote refs — future deletion candidates only

Each ref below is unprotected, is an ancestor of current `master`, has zero branch-only commits, and has zero unique paths relative to `master`. This supports **CANDIDATE FOR DELETE**, not immediate deletion. Rob must approve an exact list and dependencies must be rechecked immediately before removal.

- `codex/box-order-workflow`
- `codex/business-rule-guardrails`
- `codex/crm-22-1-ui-test-assertions-20261107`
- `codex/crm-test22-contact-save-integration-20261021`
- `codex/crm-test22-five-coverage-tests-20261021`
- `codex/crm-v10-test-13-site-agreements`
- `codex/crm-v10-test-14-acceptance-fixes`
- `codex/deployment-path-portability`
- `codex/deployment-update-safety`
- `codex/independent-gogreen-db`
- `codex/integrate-monthly-drafts-maintenance`
- `codex/october13-crm-work`
- `codex/stage4-backup-path-validation-20261025`
- `codex/stage7-post-visible-backup-20261025`
- `codex/t22-m1-semantic-verification-fix-20261022`
- `codex/t22-m1-upgrade-audit`
- `codex/t22-m2-agreement-doc-correction-20261021`
- `codex/test20-october12-recovery`
- `codex/test20-october7`
- `codex/test20-october8-recovery`
- `codex/test22`

## Local checkout and artifact inventory

### Protected and inaccessible locations

| Item | Read-only evidence | Unique-work/dependency risk | Proposal |
|---|---|---|---|
| `C:\Users\Dev\source\repos\Weekly-Logger-Search-Application` | Branch/head above; 328 pending paths: 318 under `output`, eight under `s2`, one `HANDOFF.md`, and one GoGreen source file. The staged package/recovery trees include database and backup names, which were not opened or hashed. | Protected checkout; staged manual packages, recovery material, source and handoff changes may be unique. | KEEP; never bulk-clean |
| `C:\Users\Dev\CRM-22.1-Maintenance-20261103` | Current handoff's last verified state: branch `codex/crm-22-1-maintenance-20261103`, local `a7437f0...`, 18 tracked changes plus five untracked files. Live `.git` access was unavailable in this sandbox and no broader permission was requested. | Protected original and previously unique 22-file maintenance work. Although integrated source is remote, the original remains expressly protected. | KEEP |
| `C:\Users\Dev\source\repos\GoGreenMonthlyDrafts` | Path exists; Git metadata inaccessible in the bounded sandbox. | Could be an independent GoGreen repository/workspace. | UNKNOWN / KEEP |
| `C:\Users\Dev\source\repos\Weekly Logger Search Application - test - Refactored` | Path exists; Git metadata inaccessible. | Provenance and unique work unknown. | UNKNOWN / KEEP |
| `C:\Users\Dev\source\repos\CRM UX Prototyping` | Path exists; Git metadata inaccessible. | Potential dependency for Rob's upcoming UI work. | UNKNOWN / KEEP |
| `C:\Users\Dev\source\repos\DarkPiglet` | Local protected Git metadata inaccessible; live GitHub and fresh isolated checkout were used instead. | Shared authority repository. | KEEP |

### Evidence-bearing CRM 22.1 workspaces

Sizes are non-SQLite bytes and exist only to estimate cleanup value; no database was inspected.

| Workspace | State/evidence | Size | Proposal |
|---|---|---:|---|
| `CRM22.1-Isolated-Source-Preparation-20261107-Run-01` | Clean at remote-reachable `de119331...`; eight evidence files including the GoGreen 150% fix and focused-regression TRX results. | 351,584,591 | REVIEW FOR ARCHIVE; preserve GoGreen/focused evidence first |
| `CRM22.1-Integration-Preview-20261107-Run-01` | 81 staged merge-preview paths; 14 evidence files including initial testhost failure, recovery attempts, focused CRM TRX and diagnostic logs. | 352,275,713 | KEEP until evidence archive and staged-state disposition |
| `CRM22.1-Final-Merge-Preview-20261107-Run-01` | Clean at merged `d0ee8bd...`; post-merge GoGreen TRX. | 176,823,889 | REVIEW FOR ARCHIVE |
| `CRM22.1-Broad-Safe-Regression-20261107-Run-01` | Clean at merged `d0ee8bd...`; 14 evidence files, including broad GoGreen TRX and dashboard preview. | 444,733,665 | REVIEW FOR ARCHIVE |
| `CRM221Diag1` | Failed sparse checkout: 292 staged deletions, zero non-SQLite files, no evidence files. | 0 | CANDIDATE FOR DELETE |
| `CRM221Diag2` + `D2` | Clean diagnostic checkout at merged `d0ee8bd...`; `D2` contains two diagnostic TRX and three logs. | 261,577,075 | REVIEW FOR ARCHIVE; then checkout is a deletion candidate |
| `CRM221TestFix1` + `F1` | Clean on remote/merged `7d959ed...`; `F1` contains final and initial-failure test TRX/logs. | 261,590,350 | REVIEW FOR ARCHIVE; then checkout is a deletion candidate |
| `CRM221TestIntegration1` + `I1` | One staged authorized test file in no-commit preview; `I1` contains four preview TRX and five logs. | 261,583,742 | REVIEW FOR ARCHIVE; preserve staged preview/evidence |
| `CRM221TestMerge1` | Clean at merged `0aa39d2...`; no unique TRX/log evidence found. | 3,504,485 | CANDIDATE FOR DELETE |
| `CRM221TestPostMerge1` + `P1` | Clean at merged `0aa39d2...`; `P1` contains four post-merge TRX and five logs. | 261,084,359 | REVIEW FOR ARCHIVE; then checkout is a deletion candidate |

The four short evidence roots `D2`, `F1`, `I1`, and `P1` contain 37 TRX/log evidence files in total. They are not deletion candidates until the files are preserved in an approved archive with a manifest. Published handoffs contain hashes for the key TRX files but are not substitutes for the underlying evidence if Rob/Priya want it retained.

### Documentation-only clones

The visualization root contains 78 additional Git documentation/authority/publish/verify checkouts totaling approximately 300,088,127 bytes. Seventy-six were clean; two historical Gate 1 checkouts each had one unstaged current-handoff file:

- `authority-crm-current-gate1/HANDOFF.md`
- `authority-shared-current-gate1/Shared Notes/Handoff.md`

Most clean publish/verify pairs have byte-identical current-handoff files, and all checked heads were reachable from live CRM `master`/maintenance refs or shared `main`. Examples include the exact pairs `CRM221-Publication-Docs` / `CRM221-Docs-Published-Verify-20261107` and `DarkPiglet-Publication-Docs` / `DarkPiglet-Docs-Published-Verify-20261107`. The clean historical clones, excluding the current authority/report checkouts, are **CANDIDATE FOR DELETE** after Rob approves an exact generated list. The two dirty Gate 1 clones are **UNKNOWN / REVIEW FOR ARCHIVE** because their unstaged handoff copies have unique working-file hashes and blob-reachability verification was blocked by partial-clone fetch behavior.

No accessible visualization checkout had a local-only branch tip: checked heads were detached at remotely reachable commits or on named remote branches. Git metadata for the protected/inaccessible repositories remains UNKNOWN.

## Disposition summary

| Class | Items |
|---|---|
| KEEP | Remote `master`; current project/shared handoffs and historical volumes; protected daily and maintenance checkouts; current report checkouts; unique/unresolved Option A, audit-ledger and contact-save branches; inaccessible GoGreen/refactored/UI-prototype repos. |
| REVIEW FOR ARCHIVE | Maintenance branch and documentation-only nonmerged branches; four major CRM 22.1 evidence workspaces; diagnostic/test evidence roots; staged integration previews; two dirty historical handoff clones; current protected `output`/`s2` material only through a separately reviewed exact list. |
| CANDIDATE FOR DELETE | Twenty-one fully merged remote branches; failed empty `CRM221Diag1`; clean `CRM221TestMerge1`; clean historical documentation clones whose heads/content are remote-reachable; clean diagnostic/test checkouts only after their separate evidence roots are archived. |
| UNKNOWN | Next UI working branch; inaccessible local repos; exact provenance/need for protected staged package/recovery files; two dirty historical handoff copies until archived or proven published. |

## Smallest safe future cleanup sequence

1. Rob/Priya choose the next UI branch/base and approve an exact evidence-retention policy; do not use the dirty protected project checkout as a development base.
2. Preserve `D2`, `F1`, `I1`, `P1`, the four large evidence workspaces' TRX/log/preview files, and the two dirty Gate 1 handoff files in one approved archive. Create a manifest of path, size, timestamp and existing safe hashes; exclude SQLite/database content.
3. Recheck remote refs and local statuses immediately before cleanup. Any changed SHA or newly dirty workspace returns that item to UNKNOWN.
4. First removal batch, if separately authorized: failed empty `CRM221Diag1`, clean `CRM221TestMerge1`, and an exact list of clean duplicate documentation publish/verify clones.
5. Second removal batch, if separately authorized after evidence archive: clean diagnostic/test checkouts and large build/test workspaces whose source commits are remote-reachable.
6. Remote branch cleanup, if separately authorized: remove only the exact fully merged 21-ref list above, beginning with completed test/publication branches. Do not touch the seven branch-only refs until their unique commits are archived or deliberately retained.
7. Treat the two protected checkouts and inaccessible standalone repos as separate decisions; never include them in a bulk command.

Rollback/preservation for any future authorized removal: retain this SHA/path manifest, archive unique evidence before removal, and record the archive location/hash in both handoffs. Remote-reachable source workspaces can be recreated by cloning the recorded commit. A remote branch should be deleted only after its tip SHA is recorded; because the proposed 21 refs are ancestors of `master`, their commits remain reachable from `master`, but recreating a ref must still be an explicit Rob-approved operation.

## Limitations and stop

- Live Git metadata for several protected/standalone local repositories was inaccessible; they remain UNKNOWN/KEEP rather than inferred safe.
- Some patch-equivalence/blob-reachability checks in partial clones attempted a lazy fetch that sandbox DNS blocked. Commit ancestry, branch-only counts, changed-path counts and live GitHub branch metadata were still obtained; affected uncertain items were not promoted to deletion candidates.
- SQLite/database files, credentials, email content, customer data and protected external locations were not opened or hashed.
- No historical rollover/index work was necessary; current handoffs and live Git history supplied the needed evidence.

**STOP for Rob/Priya review. No cleanup, branch deletion, archive mutation, UI work or automatic next phase is authorized.**
