---
doc_type: changelog
version: v1
status: active
authority: summary
---

# CHANGELOG

## v6
- finalized `spec-v6.md` as the current authoritative Intake spec
- expanded the final-pass process into a general plan-finalization standard
- added the four-state readiness rubric: `clear`, `usable`, `needs cleanup`, `not ready`
- required a full-document remediation loop that continues until every section is clear unless a true blocking ambiguity is named explicitly
- required a separate post-clear verification pass for contradictions, missing requested changes, unsupported claims, stale draft references, and edit-induced formatting drift
- aligned provider setup timing, provider login timing, and git completion scope with the finalized policy
- updated canonical supporting docs so `AGENTS.md` and `README.md` reflect the finalized workflow
- required quality metrics, rubric labels, and similar evaluative terms to include short concrete examples of what qualifies and what does not
- made changelog updates mandatory for every substantive canonical document change and required those updates to happen automatically as part of the same change
- replaced date-frozen best-practice wording with request-date-relative wording in the canonical spec
- removed a duplicated v6 changelog bullet so the canonical changelog is internally consistent
- added `implementation-spec-v1.md` as the task-specific Intake implementation spec with canonical entities, scope, stack, interfaces, acceptance criteria, and test approach
- added `build-plan-v1.md` as the concrete Intake build plan derived from the governance and implementation specs
- clarified document authority so `spec-v6.md` remains the only global governance doc with `authority: current`, while the implementation spec and build plan are marked `authority: derived`

## v5
- consolidated earlier routing lineage with later file-based additions into a single file-based spec

## v1
- created the first file-based capture of planning and implementation-prep policy