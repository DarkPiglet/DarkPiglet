# Test 22.1 Current Handoff 001

**Updated:** November 2, 2026  
**Status:** Documentation system established; implementation not authorized  
**Current-file rollover threshold:** 512,000 UTF-8 bytes  
**Cumulative history:** `Test-22.1-Handoff-history.md`

## Authority and scope

This handoff records verified findings, established documentation decisions, and outstanding work only. It does not approve proposed UI changes or authorize CRM source, database, configuration, operational-file, shared-handoff, or Council-record changes.

## Verified findings

### Source identity

- Local object verification confirmed exact revision `dd223e6f228c236c85b89b1246b587b2a0d1f5c2` and tree `0bfca6c87411c5f8129e35bfde28dc987c954af8`.
- The exact relevant blobs inspected included `Form1.vb` (`76fd4d41f5fc1426b8f2357efdce140d4a820848`), `Form1.Designer.vb` (`9d0525dbbe990574ed6847e3ee2358eadcad8fb7`), `Data/CRMRepository.vb` (`1f232f2fefb48630b5e2a88f93ae194631a3a6a4`), and the revision handoff (`cf9702b3e3018e0b95586430aa87ac2434832e0d`).
- Repository documentation identifies the product as `10.0.0-test.22+dd223e6f...`; it does not independently establish the label “Test 22.1.”

### Quick search

- Filtering is an in-memory, trimmed, case-insensitive substring search over loaded companies, sites, and contacts.
- Searchable fields are company name; site name, alias, structured address fields and formatted address; and contact name, email, office phone, and cell phone.
- Result rows show company headers and matching-site counts, plus site name and latest interaction. A contact/email/phone match can return a site without displaying the matching field.
- Search expands companies, preserves a surviving tagged selection, selects the first available result when needed after its timer, clears details on zero results, and restores the pre-search expansion set when cleared.

### Site Information

- The current Site Information control is a one-row grid with DT Associate, six nullable activity dates, Receiving, and Preferred Carrier.
- Receiving choices are `Boxes` and `Labels`; carrier choices are `FedEx` and `UPS`.
- Population, dirty tracking, read-only state, change detection, save, and date-activity handling directly reference the grid row and named cells.
- DT Associate has no dedicated validation. `CRMRepository.UpdateSite` preserves it only when the argument is `Nothing`; an empty string is a write and can clear it.
- Site Information date saves use `SetLatestSiteActivity` with associate attribution disabled. Other activity insertion paths can update Site.DTAssociate for the six site activity types.
- Site/contact/activity changes are committed through the existing batch transaction.

### Handoff system

- The accessible authoritative convention uses `Handoff.md` for current material and `Handoff-history.md` for cumulative history.
- The authoritative files require preservation of history and unresolved findings, verification before shortening current content, and truthful reporting of writeback failures.
- No numeric rollover threshold or independently verified interrupted-write recovery mechanism was found there.

## Established documentation decisions

- Test 22.1 documentation is isolated in this directory, outside operational CRM source and shared/Council records.
- `Test-22.1-Handoff-history.md` is the single cumulative record and never rolls over.
- Current handoffs use three-digit numbering beginning with `Test-22.1-Handoff-001.md`.
- Only current handoffs roll at a projected 512,001 UTF-8 bytes or greater; 512,000 bytes remains in the current file.
- Outgoing current content must be completely appended to verified history before the next numbered current file is created.
- Every write requires full readback, byte-count and SHA-256 verification. Any mismatch is a stop condition.
- Historical and current documentation provide context only; they do not convert proposals into approval.

## Outstanding work

- Obtain an authoritative decision on whether `dd223e6f...` is formally named Test 22.1 or retain the exact revision identifier without that claim.
- Obtain explicit requirements and approval before any quick-search field/display change.
- Obtain explicit requirements and approval before replacing or hiding any Site Information control, including the DT Associate preservation rule.
- Define focused acceptance checks only after implementation scope is approved; none are authorized or run by this setup.
- The first actual rollover remains unexercised because this current file is below the threshold. Its boundary logic and stop conditions are established in history.
- GitHub publication and remote verification remain not performed and not verified because Git/GitHub commands are prohibited for this assignment.

## Stop state

No development, build, test, database access, configuration change, operational-file change, shared-handoff change, Council-record change, Git action, or GitHub action was performed or authorized by this handoff.
