---
doc_type: implementation_spec
version: v1
status: draft
authority: derived
---

# Intake Implementation Spec v1

## Purpose

This document translates the governance rules in `spec-v6.md` into a task-specific implementation spec for the Intake system itself.

The implementation target is a working Intake engine that can analyze requests, normalize them into canonical task structures, evaluate alternatives, enforce project governance, and emit execution-ready plans and specs.

If this document conflicts with `spec-v6.md` on global governance policy, `spec-v6.md` wins. If later implementation details conflict with README or AGENTS docs, this document wins for system design and build behavior.

## System goal

Build Intake as a project-scoped planning and execution-preparation system that:
- ingests a user request
- normalizes it into a structured record
- identifies material ambiguity
- evaluates alternatives for non-trivial decisions
- registers canonical domain vocabulary
- produces stable plan and spec artifacts
- enforces finalization and changelog rules
- emits outputs consumable by human reviewers and downstream automation

## Scope

### In scope
- request normalization and structured record creation
- ambiguity detection and clarification question generation
- alternative identification and comparison
- domain entity name registration and consistency enforcement
- plan artifact generation with dependency-aware step ordering
- spec artifact generation with interfaces, requirements, and acceptance criteria
- readiness evaluation and finalization enforcement
- changelog enforcement for substantive canonical doc changes
- markdown artifact output with stable structure

### Out of scope
- runtime execution of the generated plan (Intake plans, does not execute)
- persistent database storage (first version uses file-based state)
- multi-user collaboration
- browser-based UI
- integration with specific CI/CD or deployment systems

## Canonical entities

These are the domain entities that every Intake module must use consistently.

### IntakeRecord
A normalized representation of the user's request after parsing.

Fields:
- `id`: unique identifier
- `raw_request`: original request text
- `normalized_intent`: condensed statement of what the user wants
- `steps`: extracted steps in original user-provided order
- `context`: relevant environment or project context
- `constraints`: explicit or inferred constraints from the request
- `created_at`: timestamp

### ClarificationIssue
A concrete ambiguity detected during request analysis.

Fields:
- `id`: unique identifier
- `source_record_id`: reference to the parent IntakeRecord
- `description`: what is ambiguous and why it matters
- `interpretations`: plausible interpretation paths
- `consequence_per_path`: practical impact of each interpretation
- `suggested_question`: the question to present to the user
- `status`: open, resolved, dismissed

### TaskStep
A single actionable step in the execution plan.

Fields:
- `id`: unique identifier
- `description`: what the step accomplishes
- `dependencies`: ids of steps that must complete first
- `provider_dependencies`: external services or credentials needed
- `evaluation_context`: which alternatives were considered for this step
- `order`: position in the optimized execution sequence

### Alternative
A viable approach evaluated during alternative comparison.

Fields:
- `id`: unique identifier
- `label`: short name
- `description`: summary of the approach
- `scores`: per-criterion evaluation scores
- `tradeoffs`: key tradeoffs relative to other alternatives
- `recommendation`: whether this is the recommended approach

### DomainEntity
A canonical term registered in the project vocabulary.

Fields:
- `name`: canonical name
- `definition`: what the term means in this project
- `aliases`: deprecated or alternative names
- `first_defined_in`: which document introduced the term
- `last_updated`: when the definition was last changed

### PlanArtifact
A generated plan document.

Fields:
- `id`: unique identifier
- `title`: plan title
- `source_record_id`: reference to the originating IntakeRecord
- `steps`: ordered TaskSteps
- `provider_setup`: extracted provider dependencies with setup links
- `evaluation_summary`: summary of alternatives evaluated
- `finalization_status`: readiness evaluation result
- `created_at`, `updated_at`: timestamps

### SpecArtifact
A generated specification document.

Fields:
- `id`: unique identifier
- `title`: spec title
- `source_record_id`: reference to the originating IntakeRecord
- `scope`: what is in and out of scope
- `interfaces`: defined system interfaces
- `requirements`: functional and non-functional requirements
- `acceptance_criteria`: conditions for considering the spec satisfied
- `finalization_status`: readiness evaluation result
- `created_at`, `updated_at`: timestamps

### FinalizationReport
The result of running the readiness rubric and verification pass.

Fields:
- `id`: unique identifier
- `asset_id`: reference to the plan or spec being evaluated
- `section_results`: per-section readiness state and reasoning
- `remediation_candidates`: sections flagged for automatic or manual remediation
- `verification_findings`: contradictions, stale references, or unsupported claims found
- `status`: all-clear, needs-remediation, blocked

## Technical stack

### Primary stack
- Language: TypeScript
- Runtime: Node.js
- Schema validation: Zod
- Testing: Vitest
- Output format: Markdown

### Rationale
TypeScript with Zod provides strong typing and runtime validation suitable for a policy-heavy system where schema correctness directly affects output quality. Markdown output aligns with the project's document-first philosophy. Vitest provides fast, modern testing with native TypeScript support.

### Fallback stack
- Language: Python
- Schema validation: Pydantic
- Testing: pytest

Use the fallback only if the primary stack is blocked by environment constraints.

## Module responsibilities

### RequestParser
- accept raw request text
- extract intent, steps, constraints, and context
- produce a valid IntakeRecord
- flag incomplete or malformed requests

### AmbiguityAnalyzer
- scan a normalized IntakeRecord for material ambiguity
- generate ClarificationIssue instances with concrete interpretation paths
- distinguish material from non-material ambiguity
- produce ClarificationReport

### AlternativeEvaluator
- for non-trivial decisions, identify viable alternative approaches
- score each alternative against the evaluation criteria
- produce a ranked recommendation with tradeoff documentation

### DomainVocabularyRegistry
- accept canonical term registrations
- enforce uniqueness and conflict detection
- provide lookup for consistency checking across modules
- flag stale or conflicting term usage

### DependencyPlanner
- analyze TaskSteps for inter-step dependencies
- detect dependency cycles
- reorder steps into an optimal execution sequence
- surface provider dependencies for setup planning

### ToolContextSelector
- determine the minimum tool-level and file-level context needed per subtask
- produce a ToolContext selection that can be justified
- flag requests for excessive context as a governance violation

### ArtifactGenerator
- accept analyzed request state
- produce PlanArtifact with ordered steps and evaluation summaries
- produce SpecArtifact with scope, interfaces, requirements, and acceptance criteria
- enforce stable markdown structure and canonical vocabulary

### FinalizationEngine
- evaluate each section of a plan or spec against the readiness rubric
- run automatic remediation for non-clear sections
- produce a FinalizationReport with per-section results
- enforce the full-document loop until every section is clear or a blocking ambiguity is named

### ChangelogEnforcer
- detect substantive changes to canonical documents
- verify that each substantive change has a corresponding changelog entry
- flag missing entries as enforcement violations

### IntakeCli
- thin command-line wrapper around the core pipeline
- expose commands for request analysis, plan generation, spec generation, and finalization
- produce human-readable output suitable for review

## Interfaces

### Request intake interface
Input: raw request text (string)
Output: IntakeRecord or ClarificationReport

### Clarification interface
Input: ClarificationIssue
Output: resolved clarification (user-provided narrowing)

### Domain entity registry interface
Input: register(name, definition), lookup(name), list_all()
Output: DomainEntity or conflict report

### Alternative evaluation interface
Input: decision context + constraints
Output: ranked list of Alternatives with recommendation

### Planning interface
Input: resolved IntakeRecord + evaluated Alternatives
Output: PlanArtifact

### Specification interface
Input: resolved IntakeRecord + DomainEntities
Output: SpecArtifact

### Finalization interface
Input: PlanArtifact or SpecArtifact
Output: FinalizationReport

### CLI interface
Input: command + arguments
Output: human-readable markdown or structured summary

## Acceptance criteria

The Intake implementation is correct only if:

1. A raw request can be normalized into a valid IntakeRecord with extracted steps, intent, and constraints.
2. Material ambiguity produces ClarificationIssues that name the specific ambiguity and its consequence, not generic questions.
3. Non-trivial requests produce alternative evaluation output with scored comparisons before a final recommendation.
4. Domain entity names, once registered, appear consistently across all generated outputs.
5. Plan artifacts have dependency-aware step ordering and stable markdown structure.
6. Spec artifacts include scope, interfaces, requirements, and acceptance criteria with deterministic formatting.
7. The readiness rubric can assign `clear`, `usable`, `needs cleanup`, and `not ready` states per section.
8. The finalization loop runs until every section is clear or a named blocking ambiguity prevents convergence.
9. A separate post-clear verification pass catches contradictions, stale references, and unsupported claims.
10. Changelog enforcement detects missing entries for substantive canonical doc changes.
11. Unit, integration, and golden tests pass.
12. The CLI or equivalent invocation path demonstrates the full pipeline end to end.

## Test approach

### Unit tests
- schema validation for all canonical entities
- ambiguity classification against representative fixtures
- alternative scoring computation
- domain entity registration, conflict detection, and lookup
- changelog presence checking

### Integration tests
- full request-to-plan pipeline with dependency reordering
- clarification request/response round-trip
- provider dependency extraction from multi-step requests
- finalization review plus changelog enforcement in sequence

### Golden tests
- stable section ordering in generated plans and specs
- heading normalization and blank-line discipline
- canonical vocabulary consistency across outputs

### Fixtures
- representative requests: trivial, multi-step, ambiguous, provider-dependent
- qualifying and non-qualifying examples for each readiness state
- changelog entries: present, missing, duplicated
- domain entity registration: clean, conflict, stale reference

## Notes

This implementation spec is derived from `spec-v6.md` and should be treated as a task-specific document. It does not override global governance rules. When the implementation evolves in a way that changes canonical entities or system boundaries, this document should be updated as part of the same finalization workflow that governs all canonical Intake docs.