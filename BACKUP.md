# Nebula Config Backup — 2026-05-13

Prepared for new cloud computer setup. Portable config only (no Sprite-specific config).

## Git & SSH Config

```gitconfig
[user]
    name = Dani Roxberry
    email = dani@bitoriented.com
    signingkey = 0DA7AE8DDBC158C9
[init]
    defaultBranch = main
[commit]
    gpgsign = true
```

```ssh-config
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519
    IdentitiesOnly yes
    StrictHostKeyChecking accept-new
```

SSH pubkey: `ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIGMG4k3rZUP+GlKq/e8RsBqlJQqyPXFh1vVifg5gd6em droxey@nebula-sandbox`
GitHub key #151284754, GPG key #5013682

## Device IDs

| Device | ID |
|--------|----|
| Cloud Device | dev_06a0381cc15c73658000f7bf6cc4374e |
| Cloud Computer | dev_d4e6954afcc74dc2bdba56152aff61d6 |
| BACKUP 2026-05-07 | dev_069d7511af6372018000135e9891989f |
| Fresh Cloud | dev_069fcb5c3d3875188000a19a7f6fd82a (bricked) |

## Repositories

### GitHub (droxey)
- **nebula-recipes**: droxey/nebula-recipes
- **terminal-use**: flipbit03/terminal-use
- Owner accounts: droxey, musexmachine, Tech-at-DU

### GitLab (dani@makeschool.com)
| Project | ID |
|---------|-----|
| central_logger | 82098272 |
| lazarus | 82098545 |
| PoissonDistrib | 82098560 |
| flask-nginx-rtmp-manager | 16107072 |

## Agents

| Agent | Slug | Toolkit |
|-------|------|---------|
| Gmail Agent | gmail-agent | composio:gmail |
| GitHub Agent | github-agent | composio:github |
| Calendar Agent | calendar-agent | composio:googlecalendar |
| Supabase Agent | supabase-agent | composio:supabase |
| Slack Agent | slack-agent | bot:slackbot |
| Media Agent | media-agent | builtin:media |
| Web Agent | web-agent | builtin:browser-automation, builtin:structured-search, builtin:web-scraping |
| Code Agent | code-agent | builtin:code |
| Annoyed Senior Engineer | annoyed-senior-engineer | builtin:code |
| Model Scout | model-scout | builtin:code, builtin:web-scraping |
| Manifestor | manifestor | builtin:code, builtin:web-scraping |
| Action Watchdog | action-watchdog | builtin:channels, builtin:communication |
| Itch.io Asset Scout | itchio-asset-scout | api:itch-io, builtin:code |

## Channels (Nebula)

| Channel |
|---------|
| action-items |
| nebula-config |
| manifestor |

## Triggers

| Slug | Schedule | Status |
|------|----------|--------|
| 9am-et-action-items-digest | 0 9 * * * | Active |
| daily-workspace-action-item-scan | 0 6 * * * | Active |
| action-item-scanner | 0 9,13,17,21 * * * | Active |
| weekly-memory-audit | 0 9 * * 1 | Active |
| database-query-on-demand | webhook | Active |
| backup-integrity-check | 0 9 * * * | Active |
| weekly-manifestor-research-scan | 0 9 * * 1 | Active |
| weekly-model-release-scan | 0 9 * * 1 | Active |
| daily-github-pr-issue-monitor | 0 9 * * * | Active |
| slack-channel-monitor | event | Active |

## Task Recipes (in droxey/nebula-recipes)

- tasks/daily-heartbeat
- tasks/daily-briefing-developer-trends-activity
- tasks/intake-implementation-workflow
- tasks/perceptis-manual-import-connector
- tasks/perceptyx-read-only-export-validation-and-scaffold
- tasks/airbnb-listing-workflows
- tasks/testing-project-scaffolding-policy
- tasks/weekly-memory-audit
- recipes/step-two-to-1password-migration

## Connected Toolkits & Accounts

| Toolkit | Accounts |
|---------|----------|
| GitHub | dani@bitoriented.com (ca_5VHrmFssj1GS), droxey (apn_Dphb3b7) |
| GitLab | dani@makeschool.com (ca_Fl7Cv_Qw74bZ) |
| Gmail | danielle.roxberry@dominican.edu (ca_7nwK4heQuJmv) |
| Google Calendar | droxey@gmail.com (ca_lSMivGDeQ8rL), group calendar (ca_hHeYyNwzt4rK) |
| Supabase | ca_Ay4BW9WvABa9 |
| Wachete | 4 accounts (ca_M-X8JwAL9bvy, ca_F_emtSVYrwfp, ca_l9r_dh6xLOfu, ca_lBEOzeMnpoYn) |

## Messaging IDs

| Platform | ID |
|----------|-----|
| Slack user | U02AFMZM57A (Tech @ Dominican, T029VH0R0BT) |
| Telegram | 7487885332 (@lowkeyresearch) |

## Key Constraints (from memories)

- GPG key gen requires --pinentry-mode loopback + --passphrase in non-interactive env
- npx requires --yes flag to skip prompts
- Trigger name format: [HHam Interval] Short Description
- Trigger HH must be 2-digit (09, 13, etc.)
- Memory list capped at 100 entries; weekly audit tracks overflow
- Wachete auth: POST to /thirdparty/v1/user/apilogin with userId + apiKey
- itch.io API doesn't support programmatic asset downloads

## Skills

| Skill | Notes |
|-------|-------|
| sql | Database queries |
| sql-toolkit | Supabase toolkit skill |
| find-skill | Skill discovery |
| triggers-cookbook | Trigger type selection guide |
| superpowers-mode | Strict engineering workflow |
