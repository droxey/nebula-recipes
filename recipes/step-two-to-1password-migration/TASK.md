# Step Two to 1Password Migration Checklist

## Purpose
Use this checklist to move TOTP-based two-factor authentication from Step Two into 1Password safely, one site at a time, without assuming any live sync or bulk token transfer exists.

## Use when
- You want 1Password to become the primary home for passwords, TOTP, backup codes, and recovery notes.
- You currently have working Step Two tokens.
- You want a repeatable process that reduces lockout risk.

## Rules
- Keep Step Two active until each site is tested successfully in 1Password.
- Do not start with primary email, Apple, Google, banking, or any recovery-critical account.
- Do not remove Step Two for a site until 1Password is verified.
- Do not paste TOTP secrets into chat.

## Migration order
1. Low risk accounts first: shopping, forums, streaming, newsletters.
2. Medium risk accounts next: social, SaaS, developer tools, work platforms.
3. High risk accounts last: primary email, Apple ID, Google, banking, recovery-critical accounts.

## Per-site checklist
- [ ] Confirm you can sign in to the site now.
- [ ] Confirm the username and password are correct.
- [ ] Open or create the login item in 1Password.
- [ ] Go to the site's Security or 2FA settings.
- [ ] Choose to add, reset, or change authenticator app setup.
- [ ] If the site shows a QR code, scan it with 1Password.
- [ ] If the site shows a setup key, enter it into the one-time password field in 1Password.
- [ ] Save the item in 1Password.
- [ ] Use a fresh code from 1Password to complete setup.
- [ ] Save backup codes in 1Password.
- [ ] Test a clean sign-in using the code from 1Password.
- [ ] Remove Step Two for that site only after the test succeeds.
- [ ] Mark the site complete in your migration tracker.

## Suggested tracker columns
- Site
- Category
- Risk tier
- Username or email
- Password in 1Password
- TOTP in 1Password
- Backup codes saved
- Recovery method checked
- Tested login
- Step Two removed
- Status
- Notes

## Status values
- Not started
- In progress
- Complete
- Blocked

## Blockers to watch for
- The site does not expose a new QR code or setup key.
- The site forces removal of the old authenticator before adding a new one.
- The password is outdated.
- Backup codes are regenerated and old ones stop working.
- Recovery email or phone access is missing.

## Definition of done
A site is complete only when:
- The login item is correct in 1Password.
- TOTP works from 1Password.
- Backup codes are saved.
- A fresh sign-in test succeeds.
- Step Two is removed or intentionally retained for a short overlap window.
