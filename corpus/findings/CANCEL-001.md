---
id: CANCEL-001
title: Cancellation must be as easy as signup
flow: [cancel]
segment: [consumer, smb]
category: [regulatory, trust]
confidence: regulatory
source_type: [regulatory, external-research]
status: active
owner: Aniket Kulkarni
last_reviewed: 2026-09-23
---

# [CANCEL-001] Cancellation must be as easy as signup

## Rule

Users must be able to cancel a subscription through the same channel they signed up on, in a comparable number of steps. If a user could subscribe online without speaking to anyone, they must be able to cancel online without speaking to anyone.

## Scope

**Applies to:** All consumer subscriptions, SMB self-serve subscriptions, any negative-option or auto-renewing plan sold in the US or EU.

**Does not apply to:** Enterprise contracted subscriptions with negotiated termination clauses; regulated financial or insurance products with statutory cancellation processes; B2B commercial contracts with defined notice periods.

## Evidence

The FTC's "Click to Cancel" rule (finalized 2024, phased enforcement through 2025-2026) makes it a Section 5 violation to require more steps to cancel than to sign up. The rule specifically prohibits forcing users into phone calls, chat interactions, or in-person conversations to cancel a subscription that was sold online.

California SB-313 and similar state laws (New York, Colorado) impose parallel or stricter requirements.

Baymard Institute research on subscription cancellation UX consistently finds that friction-heavy cancel flows increase negative reviews, chargebacks, and regulatory complaints — while producing only marginal short-term retention gains that erode over the following 6-12 months.

NN/g's research on trust in digital services identifies "ease of exit" as a leading trust signal: users evaluate whether they can leave *before* deciding to commit more deeply.

## Sources

- FTC "Click to Cancel" Rule (16 CFR Part 425), https://www.ftc.gov/legal-library/browse/rules/negative-option-rule
- California SB-313, https://leginfo.legislature.ca.gov/
- Baymard Institute, "Subscription Cancellation UX" (public article), https://baymard.com/blog
- Nielsen Norman Group, "Trust and Credibility on the Web," https://www.nngroup.com/articles/trustworthy-design/

## Anti-patterns

- "Call us to cancel" when signup was online
- Hidden cancel path (buried 4+ clicks deep in settings)
- Cancel requires chat with a retention agent before proceeding
- Extra verification steps at cancel that weren't required at signup (SMS code, security questions)
- Time-limited cancel windows ("only cancel during business hours")
- Cancel only available on desktop when signup was mobile-capable

## Related findings

- CANCEL-002 Retention offer placement and frequency
- CANCEL-003 Cancel confirmation must be clear about consequences
- CANCEL-004 Post-cancel state and re-engagement

## Notes

Enterprise contracted flows are genuinely exempt from FTC Click-to-Cancel because they involve negotiated commercial terms — but even there, "cancellation must match signup ease" is a strong principle. If enterprise signup involves a signed contract with sales, cancel via account manager is proportionate; if enterprise signup was self-serve for a low-tier plan, cancel must be self-serve too.
