# Nebula Recipes

This repository stores reusable Nebula task recipes, supporting instructions, and workflow documentation that can be reused across projects.

## Repository layout

- `tasks/` - task recipes grouped by workflow or project area
- `tasks/airbnb-listing-workflows/` - Airbnb listing workflow recipes and supporting docs
- `tasks/testing-project-scaffolding-policy/` - project scaffolding guidance and related task instructions
- `tasks/intake-implementation-workflow/` - Intake product implementation recipe and colocated planning docs
- `tasks/humanize-text/` - AI text detection and humanization recipe

## Included recipes

### Airbnb listing workflows
Path: `tasks/airbnb-listing-workflows/airbnb-listing-package-recipe/`

This recipe captures the default workflow for preparing an Airbnb listing photo package, including:
- reusable task instructions
- delivery rules and verification checks
- supporting agent guidance
- package documentation for future reuse


### Intake implementation workflow
Path: `tasks/intake-implementation-workflow/`

This recipe stores the canonical Intake planning set and the default implementation workflow, including:
- product and implementation planning documents
- reusable execution guidance
- a verification checklist for implementation passes

### Daily Heartbeat
Path: `tasks/daily-heartbeat/TASK.md`

Scans connected apps (GitHub, Gmail, Calendar, Slack) for updates and action items. A 3-step daily workflow that collects, synthesizes, and delivers a status report — designed to run as the first thing every day.

### Weekly Memory Audit
Path: `tasks/weekly-memory-audit/TASK.md`

Audits all Nebula stored memories for staleness, duplicates, overly verbose values, and orphaned entries. Runs every Monday at 9am ET, sends a concise audit report via email.

### Humanize Text
Path: `tasks/humanize-text/TASK.md`

Removes signs of AI-generated writing from text — inflated significance, promotional language, em dash overuse, AI vocabulary, sycophantic tone, and 17 other detectable patterns. Provides a systematic scan-and-rewrite workflow for making text sound natural and human-written.

### Superwhisper Nebula Command Prompt
Path: `tasks/superwhisper-nebula-command-prompt/TASK.md`

A compact Superwhisper custom-mode prompt that converts speech into concise Nebula agent instructions, including routing rules, low-content silence behavior, and examples for creating Nebula agents.

### Testing project scaffolding policy
Path: `tasks/testing-project-scaffolding-policy/`

This recipe stores policy and instructions related to project setup and scaffolding decisions.

## Agent Goals

Current goals for each agent in the Nebula fleet:

### Research Agent
- Research the web using search, scraping, and structured data sources for flights, hotels, shopping, news, and more
- Automate browser interactions for tasks that need login, clicking, or form submission
- Extract and organize data from web pages into structured reports

### Software Engineer
- Write, run, and debug code in the cloud sandbox using Python, Node.js, Go, Rust, and other languages
- Manage long-running services, dev servers, and background processes
- Execute data processing pipelines, build projects, and run test suites

### Siren
- Proactively protect brand reputation with daily leak and negative content scanning, DMCA, and Google de-indexing
- Make @surethingsubscription the most famous and highest-earning hotwife creator on OnlyFans/Fansly in 2026 as fast as possible
- Produce and schedule daily viral content following 2026 best practices with multi-modal outputs (image prompts, video scripts, thumbnails)
- Monitor trends, analytics, and reputation daily — auto-adjust strategy based on performance data and competitor analysis
- Drive cross-platform amplification with safe teasers to TikTok/Instagram/Reddit to funnel traffic to main platforms

### GitHub Agent
- Create and manage issues, pull requests, and code review workflows on demand
- Monitor pull requests and issues across all connected GitHub repos and flag items needing attention

### Action Watchdog
- Scan the Nebula workspace daily for action items needing user attention — login prompts, OAuth permission requests, missing credentials, confirmation dialogs, error states, and blocked workflows. Categorize each by type and urgency.
- When an action item is resolved, mark it resolved. Track resolution age to surface stale items (unresolved >48h)
- At 9am ET daily, check the count of unresolved action items. If more than 5 exist, compose and email a summary to droxey@gmail.com listing each item with category, age, and source link
- Post every discovered action item to the #action-items channel with a clear title, category tag, urgency level, and link to the source conversation

### Supabase Agent
- Run database queries and return structured results on demand
- Manage database backups and verify backup integrity periodically

### SFX Agent
- Analyze video edits and recommend precise SFX placement — identify transition points, impact moments, and emotional beats that need sound design
- Generate high-quality custom SFX via ElevenLabs sound effects API — short sounds for transitions, hits, whooshes, risers, stingers, textures
- Reason about sound design holistically — consider genre, pacing, music track dynamics, and narrative arc when choosing SFX types and placement
- Build a personal SFX vocabulary the user can reference — naming conventions, categories, and when each type works best

### Infra Agent
- Serve as the single source of truth for all of Dani's infrastructure — local homelab devices, cloud sandboxes, and remote VPS instances
- Track device specs, IPs, locations, costs, and access methods for every server
- Answer infrastructure questions (what's running where, how to access a server, what each server costs, etc.)
- Stay current — when new devices are added or specs change, update the inventory immediately
- Provide Tailscale, SSH, and Nebula device context when asked about connectivity or routing

### Radicle Integrator
- Monitor and sync multiple Radicle repositories from /home/sprite/shared/radicle, running `rad sync` proactively and reporting all new activity in real-time to #nebula-sprite-radicle
- Perform code review triage on incoming patches — summarize diffs, flag potential issues, and draft review comments via `rad patch` CLI commands
- Track and manage Radicle issues across all synced repos: surface stale issues, suggest prioritization, and help close or comment via `rad issue` CLI
- Ask Dani targeted questions about repo structure, review preferences, and automation triggers to continuously improve the Radicle workflow fit

### Agent Manager
- Proactively suggest and create specialized agents based on user needs and workflow gaps
- Audit existing agents for toolkit overlaps, stale configurations, and optimization opportunities
- Maintain a lean, efficient agent fleet — merge overlapping agents, retire unused ones
- Check GitHub daily for new or unauthorized SSH keys, personal access tokens, and suspicious workflow runs — flag anything unrecognized
- Use 1Password to track and manage credential states: identify accounts missing 2FA, store generated replacement passwords, and record recovery codes
- Send a daily summary report via email covering all monitored surfaces including manual-check items
- When suspicious activity is detected, alert immediately by email with specifics and generate a remediation checklist
- Maintain a check-history log so the user can review 30 days of monitoring activity and cross-reference false positives

### Research & Assets Agent
- Search the itch.io asset library for pixel art and game assets matching specific requirements
- Query the recall.it knowledge base to find saved articles, cards, and research
- Retrieve and summarize grain.com meeting recordings and transcripts

### X Agent
- Draft posts that maximize predicted conversation signals (replies, author-engaged replies, bookmarks, dwell time) — not raw likes
- Pair text with native media when relevant; suppress off-platform links from the main post body
- Build narrative arcs (setup → friction → resolution) in thread drafts
- Refuse generic AI-roundup and motivational-fluff drafts; ask for a specific personal proof point
- Track shipped posts via post:<id> memory entries and learn what formats/topics earn engagement for @droxey
- Run daily trigger @trigger:daily-post-suggestion — review recent activity and suggest 1 high-conversation-signal draft

### Cold Outreach Ops
- Queue approved emails through Gmail and log every touch in HubSpot against the contact record
- Research 20 target prospects daily on LinkedIn and draft personalized cold email openers
- Track campaign performance in Google Sheets with reply-rate and meeting-booked metrics
- Pause sequences automatically when a positive reply or meeting is detected

### Incident Response
- Guide users through security incident response using a structured flowchart methodology
- Research threats using OWASP, CVE databases, and cybersecurity reports
- Produce actionable incident response plans with detection, containment, eradication, and recovery steps

### Calendar Agent
- Summarize daily and weekly schedules across all connected calendars
- Find free/busy slots and create or update calendar events on demand

### Gmail Agent
- Summarize unread emails and flag high-priority messages across all connected Gmail accounts
- Search and retrieve emails by sender, subject, date range, or keyword on demand

### Slack Agent
- Send messages and notifications to Slack channels on demand
- Monitor Slack activity and surface important messages from key channels

### The Job
- Surface 5 high-signal roles per week that score on at least 2 of the 4 axes (visibility, network, density, moonshot) against the user's resume and taste
- Monitor funding announcement sources daily and queue founders who just raised for outreach before they post a public hiring page
- Draft a 90-word personalized DM for every surfaced role, referencing one specific thing the founder said in the last 30 days and one specific thing on the user's resume
- Continuously tune relevance based on user feedback edits to the prompt and taste document

### Code Turnaround Tracker
- Exclude WIP and draft PRs from all review-metric calculations to keep data fair
- Reduce median code-review turnaround time across all repos by surfacing bottlenecks
- Write weekly per-squad review metrics to a shared Google Sheet for leadership visibility
- Notify Microsoft Teams when a pull request exceeds the stale-review threshold
- Integrate with GitHub, GitLab, Google Sheets, and Microsoft Teams for full pipeline automation

### Voice Agent
- Receive raw voice-transcribed text from the user
- Remove filler words (um, uh, like, you know, sort of, kind of), stutters, and repeated phrases
- Normalize punctuation and capitalization for readability
- Restructure the content into a clean, direct command or request optimized for AI agent consumption
- Maintain the original intent and key information — never rewrite meaning, only clean the delivery

### Product Documentation Steward
- Schedule documentation review deadlines and release-note publish dates in Google Calendar
- Publish, update, and reorganize knowledge-base articles and release notes in Notion
- Notify support, success, and marketing teams via Gmail when critical documentation goes live
- Monitor GitHub issues and pull requests for user-facing changes that require documentation updates

### itch.io Asset Scout
- Return a detailed asset acquisition report listing every matching asset with title, creator, relevance score, and suggested use in the spatial command center
- Scan the user's full itch.io purchased library via the API and identify all game asset purchases
- Match identified assets against project requirements: pixel art, office furniture, desk decor, tilesets, sprites, RPG items, virtual office props
- Download matching asset files and package them into a well-organized zip archive with folder structure by asset pack

### Creative Director
- Generate images, audio, music, video, and speech on demand using AI media tools
- Transcribe audio and video files into accurate text transcripts
- Translate speech across languages and describe or edit images using vision AI
- Produce creative assets — concept art, voiceovers, sound beds, short video clips — from text prompts or reference files

### Software Forensics Agent
- Recover and analyze digital evidence from mobile app backups, SQLite databases, and cached application data
- Extract chat messages, transaction logs, and structured data from app exports and backup files
- Produce detailed forensic reports with actionable findings and recovery recommendations
- Research and apply latest mobile forensics techniques for iOS and Android data extraction

### Manifestor
- Research and synthesize comprehensive knowledge about the Human Design Manifestor type from authoritative sources
- Create practical guides for living as a Manifestor — relationships, career, parenting, energy management, boundary-setting
- Answer any Manifestor-specific questions with depth — chart mechanics, type interactions, famous examples, and common misconceptions

### Model Scout
- Match models to user use cases by evaluating requirements like latency budget, context length, reasoning depth, tool use, multilingual needs, and cost constraints
- Track new AI model releases from major providers and report on capabilities, pricing, and availability within 24 hours of announcement
- Maintain a current comparison matrix of top models across quality benchmarks, speed, cost per token, and context windows

## How to use

1. Open the relevant recipe folder under `tasks/`.
2. Review `TASK.md` for the workflow.
3. Review any companion files such as `README.md`, `AGENTS.md`, or checklists.
4. Adapt the recipe to the specific project while keeping the reusable defaults intact.

## Commit guidance

This repository is intended for durable workflow assets such as:
- task recipes
- agent instruction files
- templates and checklists
- workflow documentation

Avoid storing large generated deliverables or raw media exports here unless the repository is explicitly being used as an archive for those assets.
