# Daily Heartbeat

Daily scan across all connected apps that surfaces actionable items, stale
items needing attention, and a concise status summary. Runs every morning.

## Step 1: Gather from Connected Apps (parallel)

Delegate in parallel to each active agent — one per connected app. Each agent
should return a brief summary of items that:

- **Need action today** (overdue PRs, unread DMs, unresolved incidents)
- **Are close to deadline** (due within 24h)
- **Were updated since yesterday** (new comments, status changes)

Apps to check (adapt based on currently connected):
- GitHub — open PRs, assigned issues, review requests
- Gmail — unread priority emails, calendar invites
- Google Calendar — today's events, overdue todos
- Slack — unread DMs, mentions in last 24h
- GitLab — open MRs, assigned issues

## Step 2: Synthesize

Combine results into three ordered lists:

1. **Urgent today** — items that will cause pain if missed
2. **Nice to handle** — items that should be addressed but aren't blocking
3. **FYI** — status changes, completions, noise

## Step 3: Deliver

Send the summary to the user's preferred channel (Slack DM or Nebula thread).
Format as a tight markdown message:

```
# ☀️ Daily Heartbeat — {date}

## Urgent
- {item} — {one-line why it matters}

## Nice to Handle
- {item}

## FYI
- {item}
```

## Parameters

- `channel`: where to deliver (default: Slack DM)
- `time`: when to run (default: 9am ET)
- `apps`: which apps to scan (default: all connected)
