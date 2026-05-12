---
slug: daily-briefing-developer-trends-activity
title: Daily Briefing - Developer Trends & Activity
steps:
- description: Fetch trending developer news across focus areas
  action_key: web-search
  action_props:
    query: trending developer tools automation code review workflows site:github.com
      OR site:dev.to OR site:hackernews.com OR site:thenewstack.io
    citations: true
- description: Fetch trending AI and automation news
  action_key: web-search
  action_props:
    query: latest AI developer tools automation notification management workflow trending
      2026
- description: Fetch open GitHub PRs authored by droxey
  action_key: github-search-issues-and-pull-requests
  action_props:
    query: author:droxey is:pr is:open
    maxResults: 10
  account_id: apn_Dphb3b7
- description: Fetch open GitHub issues assigned to droxey
  action_key: github-search-issues-and-pull-requests
  action_props:
    query: assignee:droxey is:issue is:open
    maxResults: 10
  account_id: apn_Dphb3b7
- description: Fetch recent unread emails from Gmail
  action_key: gmail-find-email
  action_props:
    q: in:inbox is:unread
    maxResults: 10
    withTextPayload: false
    metadataOnly: true
- description: Compose the daily briefing digest from all gathered data
  agent_slug: nebula
  format_guide: 'Compose a concise, well-structured daily briefing digest in Slack
    mrkdwn format. Use the data from all previous steps. Sections: 1) *Trending Now*
    - 3-5 bullet points of the most relevant dev/automation/AI news with source links
    from $step.1 and $step.2. 2) *GitHub Activity* - open PRs from $step.3 listed
    with repo, title, and link; open issues from $step.4 listed with repo, title,
    and link. 3) *Inbox* - unread email count and senders/subjects from $step.5. End
    with a short one-line motivational closer. Keep it scannable and tight — no fluff.'
- description: 'Post the daily briefing to the #daily-briefing Slack channel'
  agent_id: agt_06999faa9ce275698000d9507a2ad319
  agent_slug: slack-agent
  action_key: slack-send-message
  action_props:
    channel: daily-briefing
    text: $prev
  format_guide: Post the composed briefing message from $prev to the Slack channel.
    Use the full mrkdwn-formatted text as the message body.
---

Every morning, fetches trending developer news from the web, open GitHub PRs and issues, recent emails, then composes and posts a digest to the #daily-briefing Slack channel.