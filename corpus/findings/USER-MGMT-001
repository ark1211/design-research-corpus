---
id: USER-MGMT-001
title: Destructive user actions require friction proportional to blast radius
flow: [user-management]
segment: [commercial, enterprise]
category: [trust, errors]
confidence: high
source_type: [external-research, design-system-guidance]
status: active
owner: Aniket Kulkarni
last_reviewed: 2026-09-23
---

# [USER-MGMT-001] Destructive user actions require friction proportional to blast radius

## Rule

Destructive actions in user management (deleting users, revoking access group membership, downgrading roles that remove access, transferring ownership) must present friction proportional to their blast radius. The larger the number of resources, users, or downstream systems affected by the action, the more explicit the confirmation must be. Any destructive action whose effects cannot be undone within a reasonable recovery window (7 days is a common threshold) must require typed confirmation of the affected entity's name or a similarly deliberate action, not just a click.

## Scope

**Applies to:** All commercial and enterprise admin surfaces where a single user (typically an admin) can affect the access, data, or permissions of other users. Includes user deletion, group removal, role downgrade, ownership transfer, and bulk equivalents of any of these.

**Does not apply to:** Non-destructive actions (adding users, granting additional access, view-only changes). Actions in personal or single-user contexts. Consumer contexts where the actor and affected user are the same person (e.g., deleting your own account — that's covered under cancellation findings).

## Evidence

Enterprise admin interfaces have converged on a consistent pattern for destructive actions across the last decade: the more consequential the action, the more explicit the confirmation. This isn't arbitrary — it's a response to a well-documented failure mode where admins accidentally trigger consequential actions due to muscle-memory clicks, ambiguous button labels, or misread confirmation dialogs.

Nielsen Norman Group research on error prevention identifies destructive irreversible actions as a category requiring stronger safeguards than standard undo-able actions can provide. Where undo is not possible or not immediate, prevention must be built into the action itself.

Google Workspace Admin, Microsoft 365 Admin Center, Atlassian Admin, and Auth0's Management dashboard all converge on the "typed confirmation" pattern for high-blast-radius actions (deleting a user with active resources, removing an admin, mass-deleting a group). The user must type the affected entity's name or "DELETE" verbatim before the destructive button becomes active.

The reason typed confirmation works where click-through confirmations fail: it interrupts autopilot. A click-through modal ("Are you sure? Yes / No") gets dismissed reflexively. Typing forces cognitive engagement with the specific entity being affected — the admin has to *read the name and reproduce it*, which meaningfully raises the chance they catch a mistake.

Blast radius, however, matters. Not every destructive action needs typed confirmation — that would create alert fatigue and slow legitimate work. A well-calibrated system distinguishes:

- **Low blast radius** (removing one user from one non-critical group): single-click confirmation is fine
- **Medium blast radius** (deleting a user with limited resources, downgrading one admin): standard confirmation modal with clear consequences
- **High blast radius** (deleting a user with owned resources, removing the last admin, bulk delete >10 users): typed confirmation required
- **Catastrophic blast radius** (deleting an owner, removing SSO admin access): typed confirmation + additional check (email verification, cool-down period, or requires second admin approval)

The friction should also *name* the consequences explicitly. "Delete user" is insufficient. "Delete user? This will remove access to 24 shared documents, transfer ownership of 3 groups to you, and cannot be undone" gives the admin the context to make an informed choice.

## Sources

- Nielsen Norman Group, "Error Prevention in User Interfaces," https://www.nngroup.com/articles/error-prevention/
- Nielsen Norman Group, "Confirmation Dialogs," https://www.nngroup.com/articles/confirmation-dialog/
- Atlassian Design System, User management patterns, https://atlassian.design/
- Auth0 Management Dashboard UX documentation (public), https://auth0.com/docs
- Google Workspace Admin Help — Delete or restore a user account, https://support.google.com/a/answer/33314
- Microsoft 365 Admin Center — Manage user accounts, https://learn.microsoft.com/en-us/microsoft-365/admin/

## Anti-patterns

- Same confirmation pattern for all destructive actions regardless of blast radius (over-friction on small actions, under-friction on big ones)
- Confirmation dialog that only says "Are you sure?" without naming what will happen
- Destructive button placed where non-destructive buttons usually go (e.g., primary blue button for "Delete")
- Bulk delete without a summary of what's being deleted ("Delete 47 users? Yes")
- No visible undo window, no post-action recovery path, no audit trail
- Typed confirmation that accepts partial matches or is case-insensitive when it shouldn't be
- Destructive action reversible only via support ticket

## Related findings

- USER-MGMT-002 Role changes must show what capabilities the user gains or loses (planned)
- USER-MGMT-003 Bulk actions require preview before commit (planned)
- USER-MGMT-004 Removing the last admin must be blocked, not just warned (planned)

## Notes

The 7-day recovery window is a rule of thumb, not universal. Some products (like Google Workspace) preserve deleted user data for 20+ days by default; others delete immediately. What matters is that the admin understands the actual recovery window in *your* product at the moment of confirmation, not the general industry norm.

For catastrophic actions (removing the last SSO admin, deleting a workspace owner), some enterprise products implement a cool-down or dual-authorization pattern where a second admin must approve, or the action queues for 24 hours before execution. This is stronger than typed confirmation and is worth considering for the very top of the blast-radius scale.

Bulk actions deserve their own future finding, but the principle carries: bulk destructive actions should show a clear preview of everything being affected, and confirmation should scale with the count. Deleting 3 users is different from deleting 300.
