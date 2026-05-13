---
doc_type: agents
version: v3
status: active
authority: local
---

# AGENTS

## Folder Identity
- Folder: `~/Intake`
- Category: project root
- Purpose: root-level context for AI agents working in this project

## Authority
- `spec-v6.md` is the current authoritative project spec
- If this file conflicts with the current spec, follow the spec
- This file provides local context and navigation, not overriding project policy

## What Belongs Here
- Current and prior versioned specs
- Drafts and working plans
- Root coordination documents
- Project-wide agent guidance
- Canonical project documentation such as README and CHANGELOG

## What Does Not Belong Here
- Unrelated scratch files
- Temporary outputs needed only for one isolated task
- Subtree-specific instructions that belong in a deeper `AGENTS.md`

## Local Conventions
- Keep agent-facing markdown concise and easy to scan
- Use minimal YAML frontmatter only for `doc_type`, `version`, `status`, and `authority`
- Keep policy and operational guidance in normal markdown sections
- Determine domain entity names early during planning and treat them as the canonical vocabulary for the project
- Use canonical domain entity names consistently across specs, plans, code, docs, tests, and prompts
- Apply standard language-appropriate naming conventions when declaring those entity names in code
- Maintain an `AGENTS.md` file in the root and in each subfolder
- When finalizing a plan or spec, use the readiness rubric from `spec-v6.md`, run the remediation loop until every section is clear, then run the separate post-clear verification review before declaring the asset finalized
- When a quality metric or rubric label is defined, include short examples of what qualifies and what does not so agents can pattern-match correctly
- Update canonical supporting docs after a successful finalization pass so README, AGENTS guidance, and CHANGELOG stay aligned with the authoritative spec
- Add every substantive canonical doc change to `CHANGELOG.md` as part of the same update and do not ask whether the changelog should be updated

## Important Files
- `spec-v6.md`: current authoritative spec
- `README.md`: short project entry point for the Intake folder
- `CHANGELOG.md`: chronological summary of substantive documentation and policy changes

## Agent Workflow Notes
- Read this file for root context
- Read the current spec before changing policy
- Use the readiness rubric states `clear`, `usable`, `needs cleanup`, and `not ready` when evaluating a canonical plan or spec
- Interpret each readiness state using its concrete examples, not the label alone
- Continue the remediation loop until the full asset is clear or a true blocking ambiguity is named explicitly
- After an all-clear result, run a separate pass for contradictions, missing requested changes, unsupported claims, stale draft decisions, and formatting drift
- When working in a subfolder, use the nearest `AGENTS.md` for narrower local context
