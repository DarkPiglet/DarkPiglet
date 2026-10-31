# Historical handoff rollover — approved preparation addendum (2026-10-31)

Status: Rob approved **preparation and verification only**. This addendum tightens the October 31 rollover design assignment in `Shared Notes/Handoff.md`. It does not authorize migration, publication of numbered volumes, modifications to existing handoffs, or edits to AGENTS.md. Where the earlier assignment could be read more broadly, the restrictions below control.

## Authorized scope
- Read the existing shared handoff, historical handoff, applicable AGENTS.md, and CRM handoff for context.
- Prepare a proposed partition and index in an isolated **temporary workspace only**, without changing any repository-tracked file, original checkout, staged index, Git configuration, or remote ref.
- Set the exact ordinary-volume maximum to **500,000 UTF-8 bytes**, counting generated headers, separators, and complete content. Do not confuse this with 512,000 bytes.
- Preserve all **154 complete entries** byte-for-byte and in their existing source order. Do not sort by date. Keep nested dated ### subsections with their enclosing entries. Preserve the original archive preamble and explain its placement.
- Keep `Shared Notes/Handoff-history.md` as the stable permanent index and compatibility entry point. Proposed volumes: `Handoff-history-001.md`, `Handoff-history-002.md`, etc., with 001 holding the oldest entries and the highest number current. List volumes newest-first in the index to reproduce the current source order.
- Closed volumes are immutable. The current volume stays open until adding the next complete entry, including its separators, would exceed 500,000 bytes. If one complete entry alone exceeds the limit, propose an explicitly marked oversize volume, with no splitting.
- Recalculate boundaries **after exact header generation**. The preliminary volume 002 at 499,424 raw bytes has only 576 bytes of headroom and is NOT approved as a final boundary.
- Draft (do not edit or publish) AGENTS.md instructions directing future readers to the stable index and numbered volumes. Identify any other current-handoff discovery-link changes as proposed diffs only.

## Mandatory dry-run verification report
- Record source commit/ref, Git blob SHA, SHA-256, byte length, archive preamble length, and entry manifest with original ordinal, offsets and per-entry SHA-256.
- Report exact final filenames, entry ordinal ranges, counts, generated header bytes, total UTF-8 bytes, and open/closed state.
- Check all 154 original entries appear exactly once with no omissions, duplicates, reordering or altered per-entry hashes.
- Reconstruct the original historical **body byte-for-byte**, with source preamble handled explicitly, and verify its SHA-256 and length against the original 950,661-byte source.
- Verify every ordinary volume <= 500,000 bytes, all index links and plain-text history references resolve, and the Git-reference token multiset is unchanged.
- Show the proposed index and AGENTS.md discovery text/diff; list assumptions, risks, and any failed checks.
- Verify original CRM checkout remains untouched: 327 displayed changes and 326 staged entries; do not reset, stash, pull, rebase, alter ownership or safe.directory.

## Stop condition
STOP after the dry-run report for Rob and Priya. Do not migrate, write to tracked handoffs, publish volumes/index, update AGENTS.md, change code/data, or begin P2/P3. Migration and publication require a **new explicit authorization** after review. The existing Git identity/ownership safety constraints remain in force.
