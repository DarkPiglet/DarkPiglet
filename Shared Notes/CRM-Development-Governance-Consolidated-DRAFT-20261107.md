# Development governance — consolidated review draft
**7 November 2026 | DRAFT FOR ROB/PRIYA REVIEW ONLY | Not adopted; not an instruction to Codex**

## Authority and purpose
This draft consolidates Rob and Priya's spoken review of the ten proposals in `CRM-22.1-Historical-Retrospective-Report-20261107.md`. It is a review artifact, not an amendment to AGENTS.md, a handoff assignment, or permission to execute, clean up, test, publish source, or deploy. Rob will review again **before** any independent Codex audit or adoption. Earlier approved task-specific restrictions continue to govern actual work. This document does not retroactively authorize anything.

## Cross-cutting principles
**P1 — Simplest effective, worthwhile approach.** Favor reliable, maintainable, proportionate solutions. Before complex architecture, migration or broad refactoring, assess practical simpler options and expected value versus implementation, maintenance and regression costs. Do not invent a simpler option when none is identifiable. Reconsider approaches when work stops producing meaningful value; Rob decides business priorities.

**P2 — Explain and continue safely.** Any stop or deferral must identify the triggering condition, evidence, affected work, risk, and smallest safe corrective action. Continue independent authorized work unless a shared authority, safety, data-integrity or state risk makes continuation unsafe. Do not turn a local blocker into a global stop by default.

**P3 — Proportionate oversight and truthful authority.** Do not ask again for an unchanged operation already specifically approved under unchanged conditions. Routine contained actions may proceed; significant side effects require informed Rob approval, which may be granted for a defined class of repeated operations. Critical uncontrolled risks must not proceed merely because someone consents. New material scope or risk requires a new decision. No inferred approval.

## Operational rules

### 1. Authority and source preflight
Before modifications, identify the controlling assignment, applicable handoffs and AGENTS.md, repository, branch, base/remote identity, authorized files/operations, prohibitions, and execution identity. Verify once at start and recheck the relevant facts when changed. Investigate branch drift, dirty state, or conflicting instructions; stop only affected work unless authority/shared-state integrity is uncertain. A harmless documentation-only advancement is not automatically a reason to restart an otherwise compatible task. Record enough identity evidence to reproduce the decision.

### 2. Solution selection and value checkpoint
Before a complex solution, evaluate whether a simpler viable method meets the objective and explain the tradeoffs. If none is found, state so; this does not itself justify the complex proposal. Consider benefit, risk, maintainability and regression cost. Reevaluate after repeated material failures or diminishing progress, without a rigid timer or artificial alternative requirement. Architecture or scope changes require Rob's decision.

### 3. Data classification and test fixtures
Before opening or materializing data, establish provenance, classification (fictional/disposable, protected operational, historical/recovery, or unknown), and permitted operations. Routine tests use approved fictional, disposable data. Within a verified isolated fixture and authorized test purpose, Codex may insert/update/delete fictional records, run queries and modify disposable test schema/fields as necessary, without asking per operation; this is not authority to change production schema, application requirements, or permanent fixture baselines. If the test fixture contains real data, shares writable paths with protected data, or its isolation is unverified, do not treat it as disposable. Protected/unknown data access or modification requires the applicable explicit authority and safeguards. SQLite read-only modes can still create sidecars: prove containment or use an approved safe copy. On unexpected access/write risk, stop the affected operation and explain.

### 4. Failures, retries and stop radius
A retry is appropriate only when (a) a specific corrective action exists or a transient cause is reasonably evidenced, (b) it stays within approved scope and adds no material risk, and (c) it is likely to resolve the issue or yield useful evidence. No arbitrary retry count; cease repetitive attempts without new information, diminishing value, or when authorization is needed. Preserve first failure and final outcome. Continue independent allowlisted checks unless a common authority, sensitive-data, integrity or shared-state concern prevents safe continuation. Never use a retry as implicit permission to broaden changes.

### 5. Truthful verification and test reporting
Identify what was actually executed and by whom, environment/fixture, commands or cases, denominators and results: PASS, FAIL, SKIPPED, DEFERRED, NOT RUN, NOT VERIFIED, and reported-versus-independently-verified evidence. Retain initial failures and subsequent repairs. A build, focused test, manual check, complete regression, and release acceptance are different claims. An unrun test cannot pass. Keep a concise summary and evidence references, not redundant full logs.

### 6. Workspace and exact-change control
Verify workspace, pinned source identity, local state and allowed scope before editing. Reuse a verified suitable workspace when safe; use a fresh isolated checkout when state is dirty, mixed, unsafe or ambiguous. Never discard or reset uncommitted/protected work without exact separate approval. Stage and publish only intended changes; directly necessary changes within scope may be made, but any unexpected path or material expansion must be investigated and separately authorized. Exclude operational seeds and secrets from routine build/test and publication.

### 7. Runtime permissions and side-effect thresholds
Before execution with potential writes/external effects, verify relevant settings, execution identity, writable destinations, external connections and rollback/containment proportional to risk. Reuse previously verified configuration unless material facts change.
- **Routine/minor:** expected, contained, reversible effects such as build output, temporary logs and approved disposable fictional test-data/schema operations may proceed within task scope.
- **Significant:** effects on important persistent state, external services, protected resources or difficult-to-reverse actions require Rob's explicit informed approval identifying risk, boundaries and safeguards. A specific standing approval covers unchanged repeated instances within its stated limits; generic task approval is not enough.
- **Critical/uncontrolled:** credible serious data loss, disclosure, production impact or unknown write paths without adequate safeguards: stop affected operation, protect shared state, explain and propose safer alternative. Approval alone does not eliminate an uncontrolled hazard.
Classify by real consequence, containment, likelihood and reversibility, **not merely** by whether a query or schema statement is used. No automatic escalation of permission or scope to repair an environment issue.

### 8. Separate publication and independent verification
Local completion, commit, push, merge, release and deployment are distinct statuses and permissions. For **documentation-only** publication, confirm target branch/file, authorized diff, normal commit/push, then independently fetch and verify remote identity/content; do not demand source build/integration gates. For **source** publication, apply the authorized diff/build/test/integration gates appropriate to the change, confirm target and remote state, and independently verify published result. No force-push/reset or unrelated changes by inference. On remote drift or mismatch, investigate safely and report rather than claiming success.

### 9. Evidence retention and proportionate retrospective
Before branch/workspace/file removal, inventory unique commits, unmerged/dirty work, handoffs, test evidence, database/recovery material and dependencies. Preserve necessary unique evidence with verified manifest and mapping; obtain Rob's exact removal approval separately. No cleanup is authorized by this rule. Review lessons at major phases, significant issue sequences, and preparation of a new version or test ZIP; use a brief review for routine milestones and deeper analysis only when justified. Proposed rule changes remain proposals until Rob approves them.

### 10. Constructive challenge and decision trace
Rob, Priya and Codex may challenge any decision or proposal, including their own, with evidence, proportionality, safer options and explicit tradeoffs. Minor concerns are ordinarily raised once. Significant unresolved risks warrant a clearer second challenge identifying what reasoning/safeguard is missing; do not repeatedly argue after informed approval and satisfied safeguards unless material new evidence appears. Critical uncontrolled hazards require safeguards before action. **Adequate reasoning** means understanding the issue and consequences and providing a reasonable business/technical basis, not agreeing with the assistant. Keep a short record of significant decisions: what, why, alternatives/risks, decision owner, authorization and any exception. Rob retains business/scope authority; neither a decision record nor this draft overrides safety/permission boundaries.

## Consistency audit and decisions retained
- Original proposal 8 (publication/refetch) is retained as Rule 8; original proposal 9 (evidence retention) remains in Rule 9, alongside the separately discussed milestone retrospective.
- The value-versus-effort discussion is retained as Principle P1 and Rule 2; no rigid 30-minute/two-stop trigger is imposed.
- Rule 3's disposable-fixture permission and Rule 7's significant-side-effect approval are reconciled through verified containment and actual risk; disposable schema changes are not automatically significant.
- An unchanged previously approved **specific** significant action need not be reapproved each time. Significant **new** effects require approval; critical uncontrolled hazards remain blocked.
- Stop explanations are cross-cutting; Rule 4 provides the operational test for retries and independent continuation.
- A verified existing workspace can be reused; no mandatory fresh clone on every task.
- Documentation-only publication does not require source integration testing, but remote refetch is still mandatory.
- Original source report's statement that the migration cancellation rationale is UNKNOWN applies **to its consulted authoritative records**. Rob's later conversation explains the cancellation as excessive permission/handoff problems, rework, time cost and declining value. This user-reported explanation should be captured as conversation context, not misrepresented as independently verified Git history.
- The original retrospective's distinction between technical PASS and business acceptance, including successful-send boundary, remains explicit.

## Open questions for Rob's next review (not silently resolved)
1. Specify examples and thresholds for significant versus critical side effects, especially real external emails, production DB reads, schema migration and destructive operations.
2. Decide whether any additional permanent separation of evidence retention and retrospectives improves usability, or whether Rule 9's two subsections are sufficient.
3. Decide where this framework will live **after approval**, how task-specific handoffs override or supplement it, and how changes are versioned.
4. Decide what independent audit evidence Codex should produce and whether to ask for a technical audit after Rob's next review.

## Publication and review boundary
This file is an independently reviewable draft only. Do not add it to controlling handoffs or AGENTS.md as authority, do not instruct Codex to execute it, and do not treat it as adopted. Next step: Rob/Priya reread and refine, then separately authorize Codex's independent audit. No files, branches, code, data, or historical records may be deleted or altered on the strength of this draft.
