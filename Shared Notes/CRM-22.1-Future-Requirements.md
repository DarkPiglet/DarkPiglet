# CRM 22.1 — Future requirements backlog

## Email delivery and recipient verification (deferred; recorded November 10, 2026)

**Status:** Future consideration only; not authorized for implementation.

**Need:** Beyond validating email syntax at entry, eventually distinguish whether an address can receive mail and whether it belongs to the intended contact.

**Design direction:** Keep format validity (`IsValid`) distinct from a proposed delivery-status indicator and recipient-confirmation evidence. Do not repurpose `IsValid`, because historical/imported data and downstream queries depend on its current meaning. A successful Microsoft Graph send does **not** establish delivery, and delivery does not establish recipient identity. Evaluate reliable bounce/delivery-failure signals and explicit recipient confirmation before defining statuses or automation.

**Immediate CRM 22.1 direction (separate):** Validate newly entered or edited email addresses before save, preserve historical records and compatibility, and do not add routine history-warning prompts. No schema, code, UI, or workflow changes authorized by this backlog entry.

**Before implementation:** Investigate available delivery evidence, privacy/retention and audit needs, status transitions, failure handling, and whether the benefit warrants complexity. Require Rob's explicit authorization and a separately reviewed handoff.
