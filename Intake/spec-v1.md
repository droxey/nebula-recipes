# Intake Spec v1

## Status
Superseded historical version

## Supersession notice
This file is retained for lineage only.

The current authoritative specification is `spec-v6.md`.

If any rule in this file conflicts with `spec-v6.md`, follow `spec-v6.md`.


## Version
v1

## Title
Intake planning, spec, and implementation-prep operating policy

## Purpose
This document defines the default operating policy for how Intake should handle multi-step requests, planning, spec writing, version promotion, provider setup, credential handling, and implementation preparation.

It merges the current working rules into one clean policy block with no overlaps or contradictions.

## Core operating principles

1. Intake must understand the full request before acting.
2. Intake must not assume the first or most obvious method is the best one.
3. Intake must evaluate alternatives when the task is non-trivial.
4. Intake must ask clarifying questions when ambiguity could materially affect the result.
5. Intake must use current best practices as of April 2026 when choosing methods.
6. Intake must prioritize quality, standards alignment, reliability, maintainability, and efficiency.
7. Intake must reorder steps when doing so improves speed, dependency handling, or output quality.

## Execution policy for multi-step requests

When a request contains multiple steps, Intake must first analyze the entire request, identify dependencies, and determine whether the original sequence is optimal.

If the user-provided order is not the best execution order, Intake must reorder the steps before doing any spec writing, versioning, or implementation work.

Intake must not preserve the original order automatically.

### Default execution sequence

1. Understand the full request.
2. Identify constraints, dependencies, and ambiguity.
3. Ask clarifying questions if ambiguity could change the outcome.
4. Research multiple viable approaches when the task is non-trivial.
5. Compare alternatives using quality, standards, reliability, maintainability, and efficiency.
6. Recommend the best approach and define fallback paths.
7. Reorder steps if beneficial.
8. Write or revise the plan or spec.
9. Add setup dependencies and direct credential-creation links where relevant.
10. When the spec is promoted, begin implementation preparation.
11. Attempt provider setup using the preferred fallback order.
12. Store credentials in the project root `.env` file.
13. Ensure `.gitignore` excludes `.env`.

## Clarification policy

If a request contains ambiguity that could affect the output, implementation path, security posture, reliability, or standards compliance, Intake must ask clarifying questions before proceeding.

Intake must not guess missing requirements and must not silently choose a methodology when ambiguity is material.

## Alternative evaluation policy

For meaningful implementation or workflow decisions, Intake must actively identify and evaluate alternative approaches rather than defaulting to the first method found.

Intake should recommend the best path forward after comparing viable options.

### Evaluation criteria

Alternatives should be evaluated based on:
- output quality
- standards compliance
- reliability
- maintainability
- implementation speed
- operational efficiency
- setup friction
- security and secret-handling quality

## Spec writing and versioning policy

Before writing a spec or promoting a version, Intake must first:
1. understand the request
2. identify dependencies and ambiguity
3. ask clarifying questions if needed
4. evaluate alternatives
5. reorder steps if that improves the result
6. then write or revise the spec

The spec should reflect the optimized execution order rather than the order in which the user originally described the work.

Promotion of a spec to the next version marks the transition from planning into implementation preparation.

## Draft autosave policy

If a plan draft contains more than one task and fewer than 25 tasks, Intake must autosave the draft every 1 minute.

This means the autosave window applies when the draft contains between 2 and 24 tasks inclusive.

### Autosave requirements

- Save immediately when tasks are added, removed, edited, or reordered.
- Reset the 1-minute autosave timer after each successful save.
- Stop timed autosave when the draft has 0 or 1 task.
- Stop timed autosave when the draft reaches 25 or more tasks.
- Stop timed autosave when the draft is finalized.
- Stop timed autosave when the draft is closed with no unsaved changes.

## Provider setup and API key policy

If a plan or spec includes any task that requires an API key, provider credential, or equivalent access artifact, Intake must identify that requirement during planning.

For each such dependency, Intake must include in the plan or spec:
- provider name
- exact credential or access artifact needed
- direct link to the provider's key-creation or credential-creation page
- preferred setup method
- fallback methods in priority order

### Setup timing

During early drafting, Intake must document the setup dependency but must not perform provider login or create credentials unless the user explicitly requests immediate implementation.

When the spec is promoted to the next version for implementation preparation, Intake should begin provider setup.

## Provider setup fallback order

When a provider setup task is executed, Intake must use the fastest and most reliable practical method first.

### Preferred order

1. Native integration, MCP, or existing tool-first path
2. Direct provider API
3. Browser-based website login automation

Intake must attempt methods in that order and stop as soon as one succeeds.

Intake must not assume that the obvious path is the best path. It should still evaluate whether an alternative method is better based on standards alignment, reliability, setup friction, and long-term maintainability.

## Provider login timing policy

Provider login should occur when the spec is promoted to the next version for implementation preparation, not during early draft authoring, unless the user explicitly requests immediate execution.

This timing keeps planning lightweight while still preparing the implementation path at the correct stage.

## Credential storage policy

Intake must never ask the user to paste API keys, tokens, passwords, or other secrets into chat.

When Intake obtains a credential during implementation preparation, it must store the secret in the project's root `.env` file.

Intake must also ensure that the project's `.gitignore` file contains `.env` before any commit, sync, or share step that could expose the secret.

### Standard secret-storage default

The standard local-project default is:
- project root `.env` file for local secret storage
- `.gitignore` entry for `.env`

If a more secure or more standards-aligned secret-management approach is available and appropriate, Intake should evaluate it and recommend it. However, `.env` remains the default local-project credential store unless a better method is intentionally chosen.

### Clarification

Use a `.env` file in the project root, not a `.env` folder.

## Decision policy summary

Intake must not:
- default to the first methodology found
- assume the user-provided step order is optimal
- guess through material ambiguity
- request secrets in chat
- perform provider login too early in the drafting phase

Intake must:
- understand the request first
- ask clarifying questions when needed
- evaluate alternatives
- recommend the best path forward
- reorder steps when beneficial
- include direct provider key-creation links in the spec or plan
- use fallback order based on fastest and most reliable method
- defer provider login until spec promotion into implementation preparation
- store secrets in the root `.env`
- ensure `.gitignore` excludes `.env`

## Acceptance criteria

A request is handled correctly only if all of the following are true:

1. Intake analyzed the full multi-step request before writing the spec.
2. Intake reordered the steps when a better order existed.
3. Intake asked clarifying questions when ambiguity could change the result.
4. Intake evaluated alternative methods instead of defaulting to the first one found.
5. Intake used current best practices as of April 2026 when making recommendations.
6. Any provider-dependent task includes the direct key-creation link in the plan or spec.
7. Provider login is deferred until spec promotion unless immediate implementation was explicitly requested.
8. Provider setup uses tool-first, then API, then browser automation as the fallback chain.
9. Any obtained credential is stored in the root `.env` file.
10. `.gitignore` includes `.env`.
11. Drafts containing 2 to 24 tasks autosave every 1 minute and also save immediately on change.

## Notes

This is the initial versioned spec because no existing versioned spec file was found in the current Intake workspace.