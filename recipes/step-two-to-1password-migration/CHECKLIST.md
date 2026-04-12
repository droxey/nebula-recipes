# Step Two to 1Password Migration Checklist

Use this as a plain copy/paste checklist for moving TOTP-based two-factor authentication from Step Two into 1Password safely.

## Ground rules
- Keep Step Two active until each site is fully tested in 1Password.
- Do not start with your highest-risk accounts.
- Do not remove Step Two from a site until 1Password works for that site.
- Save backup codes in 1Password every time they are shown.
- Do not paste TOTP setup secrets into chat.

## Recommended order

### Low risk first
- [ ] Shopping sites
- [ ] Forums
- [ ] Streaming services
- [ ] Food delivery apps
- [ ] Travel accounts

### Medium risk next
- [ ] Social accounts
- [ ] Developer tools
- [ ] SaaS apps
- [ ] Work platforms

### High risk last
- [ ] Primary email
- [ ] Apple ID
- [ ] Google account
- [ ] Banking
- [ ] Any account used to recover other accounts

## Per-site checklist

For each site:

- [ ] Confirm you can sign in to the site now
- [ ] Confirm username and password are correct
- [ ] Save or verify the login item in 1Password
- [ ] Open the site's Security or 2FA settings
- [ ] Choose to add, reset, or change authenticator app setup
- [ ] Scan the QR code with 1Password or enter the setup key there
- [ ] Save the TOTP in 1Password
- [ ] Verify a code from 1Password works on the site
- [ ] Save backup codes in 1Password
- [ ] Save any recovery key or recovery note in 1Password
- [ ] Test a fresh login using the 1Password code
- [ ] Remove Step Two only after successful verification
- [ ] Mark the site complete in your tracker

## Suggested tracker columns
- [ ] Site
- [ ] Category
- [ ] Risk tier
- [ ] Username or email
- [ ] Password in 1Password
- [ ] TOTP in 1Password
- [ ] Backup codes saved
- [ ] Recovery method checked
- [ ] Tested login
- [ ] Step Two removed
- [ ] Status
- [ ] Notes

## Common blockers
- [ ] Site does not show a new QR code or setup key
- [ ] Site requires disabling old 2FA before adding new 2FA
- [ ] Site requires email or SMS confirmation
- [ ] Site regenerates backup codes and invalidates old ones
- [ ] Password on file is outdated
- [ ] Recovery email or phone is no longer accessible

## Definition of done
A site is complete only when all of these are true:
- [ ] Password is saved correctly in 1Password
- [ ] TOTP works from 1Password
- [ ] Backup codes are stored in 1Password
- [ ] Login was tested successfully
- [ ] Step Two is removed or intentionally kept only as a short overlap fallback
