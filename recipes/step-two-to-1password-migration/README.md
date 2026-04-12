# Step Two to 1Password Migration

A practical, safety-first recipe for moving TOTP-based two-factor authentication from Step Two into 1Password.

## What this is

This recipe is for a full cutover from Step Two to 1Password. It assumes there is no universal bulk transfer or live sync for TOTP tokens, so migration happens site by site with verification at each step.

## What is included

- `TASK.md` - reusable migration recipe
- `CHECKLIST.md` - plain Markdown checklist for direct copy/paste use

## When to use this

Use this recipe when:
- Step Two is your current authenticator
- You want 1Password to become the primary home for passwords, TOTP, backup codes, and recovery notes
- You want a repeatable process that reduces lockout risk

## Core rules

- Keep Step Two active until each site is fully tested in 1Password.
- Do not start with high-risk accounts.
- Do not remove Step Two from a site until 1Password works for that site.
- Save backup codes in 1Password whenever they are shown.
- Migrate critical recovery accounts last.

## Recommended migration order

1. Low risk accounts: shopping, forums, streaming, newsletters
2. Medium risk accounts: social, SaaS, developer tools, work platforms
3. High risk accounts: primary email, Apple, Google, banking, and recovery-critical accounts

## Per-site flow

1. Confirm you can still sign in to the site
2. Verify username and password are saved in 1Password
3. Open the site's 2FA settings
4. Add or reset authenticator app setup
5. Save the TOTP in 1Password
6. Verify a code from 1Password works
7. Save backup codes and recovery notes
8. Test a fresh login
9. Remove Step Two only after successful verification
10. Mark the account complete in your tracker

## Definition of done

A site is fully migrated only when:
- the password is correct in 1Password
- TOTP works from 1Password
- backup codes are stored
- a fresh login test succeeds
- Step Two is removed or intentionally kept only for short overlap

## Notes

This recipe does not claim unsupported automatic token transfer or live sync. It is designed for realistic, low-risk migration.
