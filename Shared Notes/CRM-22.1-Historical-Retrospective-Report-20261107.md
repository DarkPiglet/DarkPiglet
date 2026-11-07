# CRM 22.1 Historical Retrospective — November 7, 2026

## Executive summary

CRM 22.1 ultimately produced useful corrections, a safer evidence discipline, a bounded maintenance line, and verified focused results. It also accumulated a costly trail of abandoned or superseded approaches, repeated environment and publication stops, an unfinished schema-25 migration, and multiple cases where the test or procedure was wrong before the application was. The record does not support a simple conclusion that either more controls or fewer controls would have solved the problem. The most effective controls were precise and early: pin the authority and source ref, classify data before access, isolate the exact diff, define writable paths, preserve failed evidence, and independently verify publication. The least effective controls were repeated whole-process restarts, one-step approval loops for routine retries, and global stops triggered by a problem that did not affect other independent work.

The canceled migration and the later schema-24 Option A work should be treated as design and cautionary evidence, not as deployable product. The authoritative record states that the November 2 migration was canceled, but does not state why. The retrospective therefore leaves the cancellation rationale **UNKNOWN** rather than assigning a motive to Rob, Priya, or Codex.

The strongest recurring technical lesson is that lifecycle semantics must be stated before code and tests. Draft-time follow-up recording passed earlier technical audit work but later failed the November 5 business rule that history be recorded only at the successful-send boundary. Similarly, nullable dates, blank email handling, and byte-identical export needed explicit acceptance semantics. Focused tests eventually passed after correction, but those results must not be represented as a full regression or release decision.

The recommended future operating model is a lean ten-rule system. It retains hard stops for authority ambiguity, unsafe data, unexpected diffs, uncontrolled writes, and publication mismatch, while adding bounded retries, value checkpoints, independent-test continuation, and explicit exception records. These are proposals only; this report does not adopt any rule or authorize implementation, cleanup, release, or deployment.

## Authority, scope, and method

This report executes only `CRM-22.1-Historical-Retrospective-ReadOnly-Authorized-20261107.md`. It is based on:

- the current CRM `HANDOFF.md` and shared `Shared Notes/Handoff.md`;
- the permanent historical index and numbered volumes 001–003, used only where historical evidence was needed;
- the November 5 consolidated investigation and correction-completion reports;
- the November 7 cleanup inventory report;
- read-only Git commit/ref/diff metadata for the current CRM remote history and the seven identified unique-history refs.

No application source, test, database, package, deployment, branch, historical volume, or protected workspace was changed. No SQLite file was opened, copied, hashed, or queried. Reported test results below are historical evidence; no build or test was rerun for this retrospective.

Evidence labels used here:

- **Verified metadata** — observed directly in Git refs, commits, path diffs, or hashes during this assignment.
- **Recorded result** — reported in an authoritative handoff/report, but not rerun during this assignment.
- **Inference** — a conclusion drawn from multiple recorded facts and identified as such.
- **UNKNOWN** — the available authoritative record does not establish the answer.

## Coverage and limitations

Coverage begins with the October 19 recovery/correction work, continues through the Test22 migration/settings efforts, the schema-25 audit-ledger attempt, schema-24 Option A P1–P3, the canceled November 2 migration, the bounded maintenance/GoGreen work, the November 5 consolidated investigation and corrections, and the November 7 source/test integrations and cleanup inventory.

Important limitations:

- The record contains no authoritative account of the reason the November 2 migration was canceled.
- Private conversations and intentions are not evidence. Priya's views are represented only where the handoffs or supplied requirements document them.
- Some old branches contain mixed source and handoff history. Patch-equivalence alone cannot prove full semantic equivalence or disposability.
- Historical PASS results vary in independence. Some were reported by the implementing session, some were repeated in isolated integration or post-merge workspaces, and some were manual/interactive observations.
- Focused suites, acceptance cases, and visual checks do not establish a full regression, package readiness, or release readiness.
- The November 7 inventory deliberately avoided operational/customer data and therefore left some local material classified UNKNOWN.

## Condensed chronology

| Period | Decision or action | Result and evidence | Retrospective assessment |
|---|---|---|---|
| Oct 19 | Recovery comparison and correction investigation began with strict preservation requirements. | A read-only SQLite connection created WAL/SHM sidecars on copied evidence; main database hashes stayed unchanged. Later work used disposable copies. | The preservation goal was correct. The first method underestimated SQLite side effects; the corrected disposable-copy method was the right simplification. |
| Oct 19–20 | Recovery dry-run and correction harnesses were developed and exercised. | One dry run failed from a stale variable reference (`key[1]` instead of `k[1]`); the harness omitted a traceback. Later disposable correction verification recorded 216 changes and 350 field assertions. | A preventable harness defect and weak diagnostics cost time. Preserving the failed evidence made the later result more credible. |
| Oct 20–21 | Contact-save behavior was corrected and followed up on isolated branches. | The initial controlled launch exposed collateral normalization writes. Source commits `d502271` and `149b4a7` were kept separate; later integrated work addressed related behavior. | Stopping production promotion was justified. The branches remain evidence-bearing until semantic equivalence is reviewed, not merely assumed from later commits. |
| Oct 21–27 | Test22 migration, settings, packaging, and acceptance preparation proceeded through repeated preflights. | Work repeatedly stopped on destination identity, ACL/launcher, settings-import restrictions, and writable-path containment. Preparation improved, but controlled acceptance could not start safely under the stated constraints. | Several stops protected data and configuration. The absence of an upfront writable-path/settings contract caused avoidable loops. |
| Oct 27 | A schema-25 immutable audit-ledger design was implemented on a dedicated branch. | Compilation failed because a command identifier shadowed a helper (`BC30980`); 0/9 tests ran. The incomplete work was preserved at `d7df8c7`. | The attempt was too far into implementation before proving the simplest design and compile path. Preservation was correct; retry without renewed value review was not warranted. |
| Oct 28 | The audit baseline was reassessed. Two options were articulated: schema 24 plus an external signed report, or schema 25 database-contained traceability. | Rob selected/reconciled schema-24 Option A with P0–P9 and an explicit external trust boundary. | This was a sound simplification: it separated operational history from external assurance and avoided an unnecessary migration dependency. |
| Oct 29–Nov 1 | Option A P1–P3 were implemented and verified in stages. | Initial P1 was blocked by sandbox/NuGet configuration. A namespace collision was fixed with `Global.System.Data.ConnectionState.Open`; focused companion and CRM tests recorded PASS. P2/P3 focused checks also recorded PASS. Publication required later clean-Dev workflows. | The staged technical work produced valuable evidence. However, draft-created follow-up audit behavior encoded a business assumption that November 5 later rejected. Technical PASS did not prove correct lifecycle semantics. |
| Nov 2 | CRM migration was canceled. | Current authoritative handoffs explicitly mark the November 2 migration canceled and older migration authorizations historical. | Cancellation is authoritative. Its rationale is UNKNOWN, so this report does not retrospectively declare it right or wrong. The work remains useful design evidence. |
| Nov 3 | Bounded maintenance/GoGreen work was re-scoped from a verified source milestone. | Initial attempts stopped on baseline identity and then on the tracked `Database/CRM_seed.sqlite`. A narrowly authorized read-only inspection established that the seed was production-scale/unsanitized, causing a global stop. A fictional fixture was later authorized and maintenance proceeded. | The final fictional-fixture approach was correct. The repository should have classified/excluded the operational seed before checkout/build; reaching an inspection exception was unnecessary exposure and process cost. |
| Nov 3–4 | Site, Contact, visual, exporter, and regression stages were run sequentially with targeted repairs. | The record preserves intermediate failures, including an interactive 3 PASS / 3 FAIL / 1 NOT VERIFIED state and later exporter failures. Targeted work eventually recorded final maintenance 14/14 and visual 2/2 PASS. | Preserving the failure sequence is a strength. The results are focused, not a full regression or release verdict. Sequential gating improved isolation but sometimes stopped independent safe work unnecessarily. |
| Nov 5 | A consolidated investigation examined A12, A02, A03, and A09. | Recorded failures: A12 date/history semantics; A02 nullable-date clearing; A03 blank email remained active; A09 semantic equality but byte inequality from XLSX ZIP metadata. | The report correctly distinguished business behavior, persistence, activation, and byte identity. It provided a narrow correction target rather than a broad rewrite. |
| Nov 5 | Corrections were implemented in isolation. | Recorded final results: A12 6/6, A02 2/2, A03 4/4, A09 deterministic 1/1 plus class 15/15. Earlier A02 test-context failures and A03 casing repair were retained. A12 workplace-crash behavior remained unverified. | Strong evidence discipline and bounded repair. The successful-send boundary was corrected by removing draft-time recording; no unsupported send-success recorder was invented. |
| Nov 7 | Maintenance and two UI-test corrections were integrated through isolated preview and post-merge verification. | Verified source milestones include maintenance source `09c3786`, UI-test correction `7d959ed`, and merge `0aa39d2`; post-merge focused UI results were recorded as 5/5. Current `master` later advanced only through documentation to `2e8ceba`. | The isolated merge/refetch pattern is the strongest publication model in the history. The handoffs correctly retain deferred fixture-incompatible, manual, external, and crash cases. |
| Nov 7 | A read-only cleanup inventory reconciled branches and local workspaces. | Twenty-one refs were fully merged candidates; seven refs retained branch-only history. Evidence workspaces contained 37 TRX/log files. No cleanup occurred. | Correctly separated inventory from deletion authority. Unique-history and dirty protected workspaces must remain preserved pending an exact archive/removal decision. |

## Decision and error matrix

| Area | What happened | Primary contributor category | Control that worked | Simpler or better alternative |
|---|---|---|---|---|
| Authority and branch identity | Work sometimes encountered stale, dirty, divergent, or ambiguous workspaces. | Process/state management; not attributable to one actor. | Stops prevented accidental overwrite, merge, reset, or publication from the wrong base. | At assignment start, pin owner, branch, commit, allowed paths, and a fresh isolated checkout; do not reuse protected dirty workspaces. |
| SQLite evidence safety | A read-only connection created sidecars; a tracked seed was later found production-scale/unsanitized. | Codex method assumption plus repository data-classification gap. | Main hashes were preserved; later work used disposable fictional fixtures and excluded the seed. | Classify every database artifact before materialization; use static repository metadata first; require a fictional fixture for all routine build/test paths. |
| Recovery harness | A stale variable and missing traceback obscured the first dry-run failure. | Codex implementation/diagnostic error. | Failure was preserved and corrected before production action. | Run the smallest fixture case first and always capture traceback, inputs, outputs, and zero-write proof. |
| Migration/settings readiness | Repeated stops on destination, ACL, launcher, settings, and writable paths. | Incomplete upfront contract; some environmental constraints. | No unsafe migration or uncontrolled write occurred. | Define destination identity, settings source, write routes, rollback, and launch command in one preflight artifact before any build or acceptance attempt. |
| Schema-25 audit ledger | Implementation began before compilation/value were proven; compile failed and tests did not run. | Architecture sequencing and a Codex code defect. | Branch isolation and preservation prevented contamination. | First approve objective and trust boundary; compile a minimal vertical slice; prefer schema 24 plus signed external evidence unless database-contained traceability is demonstrably required. |
| Option A P1 environment | NuGet/sandbox and namespace issues blocked the first pass. | Environment plus Codex namespace error. | Bounded diagnosis and a one-line explicit namespace fix led to focused PASS. | Verify restore/config context and compile a minimal target before a broader stage. Allow one routine rerun without a new approval when inputs and scope are unchanged. |
| Business lifecycle semantics | Draft-time follow-up recording was technically implemented and tested, then later found inconsistent with the successful-send rule. | Requirement-to-test gap across decision makers and implementation. | November 5 investigation isolated the discrepancy; correction removed the premature write. | Write lifecycle invariants before code: trigger, transaction boundary, idempotency, failure behavior, and forbidden earlier writes. Tests must assert those invariants. |
| UI tests | Some initial assertions used the wrong lifecycle/site-edit context; one casing issue required repair. | Test design error, not necessarily application failure. | Failures were retained and tests were corrected without weakening the intended behavior. | Demonstrate the state transition manually or through a minimal probe before encoding the assertion; distinguish harness failure from product failure. |
| Export byte identity | Semantic XLSX equality was mistaken for sufficient evidence until ZIP metadata differences were identified. | Acceptance-criterion ambiguity. | A deterministic byte-identity case and broader class tests were added. | State whether the contract is semantic equality or byte identity at assignment approval; if byte identity is required, control archive timestamps/order from the start. |
| Publication | Git ownership, DNS, partial clones, and dirty handoffs caused repeated publication stops or delayed verification. | Environment and workspace design; occasional status uncertainty. | Later clean Dev clones, exact allowlists, normal pushes, and independent refetches worked. | Separate implementation from documentation publication, use a clean full-enough checkout, and do not claim publication until remote ref plus fetched blob hashes are verified. |
| Approval cadence | Some work waited for narrowly sequenced approvals even when a retry or independent check did not change risk. | Governance design; Rob retained final authority, Codex followed the written gates. | Material changes remained under explicit control. | Require new approval only for material scope, data, source, architecture, or external-state changes. Allow bounded same-input retries and independent read-only checks. |
| Global versus local stops | One blocked case sometimes halted all work, even when other cases were independent and safe. | Procedure design. | Global stops reduced accidental scope expansion. | Define stop radius: stop the affected case/workspace; continue independent allowlisted work unless the trigger concerns authority, data integrity, or shared state. |

## Fair assessment of decisions and actions

### Rob

Rob consistently retained final authority, required preservation of operational data and evidence, and repeatedly narrowed source/publication scope. Those decisions prevented destructive history repair, unreviewed migration, uncontrolled database work, and release claims unsupported by evidence. The later demand for isolated checkouts and independent remote verification materially improved reliability.

The record also shows a high-friction approval cadence: work was often divided into small sequential authorizations, and constraints were sometimes clarified only after an attempted stage exposed the missing rule. That structure contributed to repeated rereads, stops, and publication loops. This is a process effect, not evidence of bad intent. A leaner approval model can preserve Rob's final control while pre-authorizing routine same-scope retries and independent safe checks.

### Priya

The authoritative record contains requirements and correction material associated with Priya, including business feedback that helped expose acceptance gaps. It also records points awaiting Rob/Priya review. It does not contain a reliable account of Priya's private decisions, the migration-cancellation rationale, or individual responsibility for the repeated loops. No stronger attribution is justified. Future records should capture the exact approved business invariant and decision owner without attempting to reconstruct private intent later.

### Codex

Codex correctly stopped on many high-value conditions: unexpected writes, dirty or ambiguous workspaces, unsafe data, failed verification, branch drift, and publication mismatch. It preserved incomplete schema-25 work, intermediate test failures, TRX/log evidence, and protected checkouts instead of hiding or overwriting them. Later isolated merge and refetch verification was disciplined and effective.

Codex also introduced or amplified avoidable problems: the recovery harness stale-variable error and weak traceback capture; an incorrect schema-version assumption during disposable preparation; namespace and command-shadowing compile errors; test assertions that did not match the actual UI lifecycle; and procedures that sometimes treated a local blockage as a global stop. Some Git/DNS/NuGet/ACL failures were environmental, not Codex mistakes, but the response could often have been a bounded retry or continuation of independent work rather than a full process restart. Status language also needed later correction where local completion was not yet remote publication.

## Root-cause themes

1. **Contracts were sometimes discovered through execution.** Data classification, writable paths, lifecycle boundaries, and byte-identity requirements should have been explicit inputs.
2. **Safety controls were stronger than stop-radius design.** The process knew when to stop but not always what could safely continue.
3. **Workspace state became part of the problem.** Protected dirty checkouts, sparse/partial clones, and documentation mixed with source increased verification cost.
4. **Technical PASS was occasionally mistaken for business correctness.** Draft-time audit history is the clearest example.
5. **Test truth needed finer labels.** A reported focused PASS, an isolated rerun, an interactive observation, and a full regression are different evidence classes.
6. **Architecture was considered before value was fully fixed.** Schema 25 increased complexity before the external-trust-boundary alternative was settled.
7. **Publication was not treated as a separate deliverable soon enough.** Clean-identity commits plus independent refetch should be the standard endpoint.
8. **Historical preservation worked, but at growing operational cost.** The retained branches and workspaces now need an explicit archive plan before any cleanup.

## Proposed lean operating rules

These ten rules are proposals for Rob/Priya review. They are not adopted by this report.

| # | Rule | Trigger and required action | Owner / checker | Stop threshold | Required evidence and exception handling |
|---|---|---|---|---|---|
| 1 | Authority and ref preflight | Before any task, record controlling assignment, repository, branch, remote tip, base commit, allowed paths, prohibited actions, and identity. | Codex records; Rob resolves ambiguity. | Stop for missing authority, ref drift, wrong identity, or unexpected dirty state. | Preflight block in handoff/report. Exception requires Rob's explicit written scope change. |
| 2 | Minimal-solution value checkpoint | Before schema, architecture, migration, or broad refactor, compare the smallest viable alternative and expected operational value. Recheck after two material stops or 30 minutes without new evidence. | Codex proposes; Rob/Priya decide business value. | Stop the approach—not all independent work—when value or objective is unclear. | Decision table with chosen/rejected alternatives. Exception records why added complexity is necessary. |
| 3 | Data and fixture contract | Before materializing or opening any database/data artifact, classify it and state allowed operations. Routine tests use an approved fictional fixture. | Codex records; Rob/Priya approve sensitive-data exceptions. | Global stop for unknown classification, operational/customer data exposure, or uncontrolled writes. | Classification, provenance, expected hash/size where authorized, and write-containment proof. |
| 4 | Bounded retry and stop radius | One same-input retry is allowed for transient environment/tool failures; independent allowlisted checks may continue. | Codex executes; handoff records. | Stop affected case after retry; global stop only for authority, integrity, sensitive data, or shared-state risk. | First failure, retry conditions, result, and explicitly deferred cases. No silent repetition. |
| 5 | Truthful result taxonomy | Label every result as reported, independently rerun, manual, focused, full-suite, deferred, failed, or not verified. Preserve pre-repair failures. | Codex; reviewer checks wording. | Stop publication if evidence class or denominator is unclear. | Commands/cases, counts, artifact IDs/hashes, environment, and limitations. |
| 6 | Exact diff and isolated workspace | Source work uses a fresh checkout at the pinned ref, an allowlist, and seed/data exclusion. Stage only exact authorized paths. | Codex; Git diff is checker. | Stop for unexpected path, base change, dirty tree, or mixed documentation/source state. | Pre/post status, staged diff, hashes, and parent commit. Exception must name exact additional paths. |
| 7 | Runtime and write-route contract | Before GUI, package, migration, or acceptance launch, enumerate settings source, destinations, every writable route, external effects, rollback, and kill conditions. | Codex drafts; Rob/Priya approve operational effects. | Stop launch for any unresolved route or external action. | One launch manifest; no repeated rediscovery across stages. |
| 8 | Publication separation and refetch | Treat commit/push as a separate documentation or source publication step. Verify remote tip, refetch into an independent checkout, and compare exact paths and hashes. | Codex publishes and independently checks. | Stop without repair for remote drift, mismatch, or uncertain content. | Local commit, remote commit, fetched blob hashes, clean status, and limitations. |
| 9 | Evidence retention gate | Before deleting any branch/workspace, prove merged or archived status and preserve unique commits, reports, TRX/logs, and decision context. | Codex inventories; Rob authorizes exact removal list. | Stop deletion for unique history, dirty protected state, missing manifest, or UNKNOWN data. | Archive manifest plus ref/path mapping. Deletion authority must be separate and exact. |
| 10 | Respectful challenge and decision record | When a rule creates repeated cost or conflicts with the objective, Codex must state the evidence, simpler option, risk, and requested decision once. | Codex raises; Rob decides; Priya confirms business semantics where applicable. | Stop only the disputed path if the decision is material and unresolved. | Concise decision/exception entry; no inferred consent and no attribution beyond the record. |

## Retention implications

The following is a preservation assessment, not cleanup authorization.

| Unique-history ref / evidence set | Current verified metadata | Retention assessment | Reason / prerequisite before any future removal |
|---|---|---|---|
| Maintenance ref at `de53aa9` | 14 branch-only commits; one unique path (`HANDOFF.md`) relative to current master. | **REVIEW FOR ARCHIVE; KEEP now.** | Source appears integrated, but the unique chronology must be captured in an archive manifest before ref removal. |
| Audit-ledger ref at `1228cf3` | 17 branch-only commits; 20 unique paths including schema-25/audit-ledger source and tests. | **KEEP as immutable caution/design evidence.** | Incomplete and not deployable, but it documents the canceled database-contained approach and failure state. |
| Contact-fix ref at `d502271` | One branch-only commit; four unique paths in ref comparison. | **KEEP pending semantic-equivalence review.** | Later integrated commits do not by themselves prove this mixed source/handoff patch is disposable. |
| Contact-follow-up ref at `149b4a7` | Two branch-only commits; four unique paths; `git cherry` reports one equivalent and one non-equivalent patch. | **KEEP pending exact patch/context review.** | Preserve until the source behavior and handoff context are mapped to current master. |
| Option A ref at `e2f33d7` | 56 branch-only commits; 24 unique paths; 55 positive patches by `git cherry`. | **KEEP / archive as a coherent historical line.** | Contains P1–P3 technical audit work and canceled-path context. It is not an active release branch. |
| Synthetic-package ref at `5d25089` | One branch-only commit; unique path is `HANDOFF.md`. | **REVIEW FOR ARCHIVE; KEEP now.** | Capture the package/fixture decision chronology before removal. |
| Manual-findings ref at `07e779f` | Seven branch-only commits; unique path is `HANDOFF.md`. | **REVIEW FOR ARCHIVE; KEEP now.** | Preserve manual findings and limitations in an indexed archive first. |
| Evidence workspaces `D2`, `F1`, `I1`, `P1` | Cleanup inventory found 37 TRX/log files. | **KEEP pending manifest and approved archive.** | Test artifacts are needed to support historical PASS/FAIL claims. Hash and map them before any move/removal. |
| Protected dirty CRM checkout | Local Option A lineage; 326 staged and two unstaged paths; remote branch divergence recorded. | **KEEP untouched.** | It is not a safe base and must not be reset, merged, rebased, or cleaned without separate exact authority. |
| Historical index and volumes 001–003 | Permanent indexed history with recorded immutable hashes. | **KEEP permanently.** | They are the authoritative historical evidence path; this assignment does not modify them. |
| Twenty-one fully merged remote refs and clean duplicate documentation clones | Inventory found zero unique commits for the refs; most clones were clean/remotely reachable. | **Future candidates only.** | Require an exact approved list, fresh remote comparison, and evidence-manifest completion. No deletion is authorized here. |

The safest future archive sequence is: preserve immutable ref tips and commit graphs; hash and index unique reports/TRX/logs; map source-equivalent work to current master; record UNKNOWNs; obtain Rob's exact removal authorization; then perform cleanup as a separate task with post-action verification. Until then, all seven unique-history refs and evidence-bearing workspaces remain preserved.

## Unresolved questions

- Why was the November 2 migration canceled, and which business or operational criterion controlled that decision? **UNKNOWN.**
- Which branch should become the next authorized UI working branch? **UNKNOWN / requires Rob authorization.**
- Are `d502271` and the non-equivalent portion of `149b4a7` fully represented semantically in current master? **Not established.**
- Should the schema-25 and Option A lines be retained as remote branches, tagged immutable snapshots, or exported archives? **Requires an explicit retention decision.**
- Which of the 37 TRX/log files are canonical evidence versus duplicates? **Requires manifesting; no removal before that work.**
- The A12 workplace-crash scenario, fixture-incompatible cases, and several external/manual behaviors remain **NOT VERIFIED / DEFERRED**.
- No full regression, package-readiness, release-readiness, or deployment conclusion is established by the focused results summarized here.

## Priority recommendations

1. Review and, if acceptable, adopt the ten lean rules through a separate explicit decision; do not treat this report as adoption.
2. Before further UI work, select and pin the exact branch/base and use a clean seed-excluded workspace.
3. Write lifecycle invariants and acceptance evidence classes before the next correction, particularly for send/history/date behavior.
4. Create a separate archive/retention assignment for the seven unique-history refs and 37 TRX/log artifacts; authorize no deletion until its manifest is reviewed.
5. Keep schema-25 and Option A historical work out of release scope unless a new business objective explicitly justifies revisiting it.
6. Continue to require independent refetch verification for every source or documentation publication.

## Independent quality review

A separate final review of this report checked the chronology against the current handoffs, numbered history, November 5 reports, cleanup inventory, and current Git metadata. It confirmed that:

- the migration-cancellation rationale is not invented;
- Priya is not assigned actions or motives absent from the record;
- Rob's safety decisions and approval-friction effects are both represented;
- Codex successes, preventable errors, and environmental failures are distinguished;
- historical failures remain visible before their repairs;
- focused PASS results are not promoted to full regression or release claims;
- all seven unique-history refs and evidence workspaces receive a retention assessment;
- exactly ten proposed rules are stated with triggers, owners/checkers, stop thresholds, evidence, and exception handling;
- no cleanup, implementation, rule adoption, source/test/database action, build, test, package, release, or deployment is authorized or implied.

Residual uncertainty remains where the authoritative record is silent or semantic equivalence has not been proven. Those items are labeled UNKNOWN or not established above.

**STOP for Rob/Priya review. No automatic next phase.**
