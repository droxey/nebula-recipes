# Weekly Memory Audit

Audits all stored memories for staleness, duplicates, overly verbose values,
and orphaned entries. Runs every Monday morning.

## Step 1: List All Memories

Run a full memory listing. Capture:

- Total count
- Breakdown by category (resource_mapping, learned_constraint, user_preference, api_pattern)
- Breakdown by connected app (github, slack, gitlab, googlecalendar, general)

## Step 2: Flag Problems

Scan each memory for:

### Staleness
- Resource mappings to IDs that no longer resolve (e.g., deleted channels, repos, users)
- Learned constraints that contradict current behavior
- Preferences for tools or flows that have changed

### Duplicates
- Same key with identical value → remove one
- Same key with different values → flag for user to resolve
- Near-duplicate keys pointing to same value → merge

### Verbosity
- Values over 500 characters that could be shorter
- Memories that embed full API responses instead of just the mapping

### Orphans
- Memories for apps that are no longer connected
- Channel-scoped memories for archived/deleted threads
- Resource mappings where the parent resource no longer exists

## Step 3: Generate Report

Produce a markdown report with:

1. Summary stats (total, clean, flagged)
2. Per-category flag counts
3. Top 5 recommended deletions
4. Top 5 recommended merges/updates
5. Full flag list (collapsible)

## Step 4: Deliver

Email the report to the user. Subject: "Weekly Memory Audit — {date}"

Offer inline actions: "Delete X memories", "Merge Y and Z", "Show me the full list"

## Parameters

- `threshold_days`: memories older than N days without access are stale candidates (default: 90)
- `max_value_length`: flag values longer than this (default: 500)
