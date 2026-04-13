# Nebula Recipes

This repository stores reusable Nebula task recipes, supporting instructions, and workflow documentation that can be reused across projects.

## Repository layout

- `tasks/` - task recipes grouped by workflow or project area
- `tasks/airbnb-listing-workflows/` - Airbnb listing workflow recipes and supporting docs
- `tasks/testing-project-scaffolding-policy/` - project scaffolding guidance and related task instructions
- `tasks/intake-implementation-workflow/` - Intake product implementation recipe and colocated planning docs

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

### Testing project scaffolding policy
Path: `tasks/testing-project-scaffolding-policy/`

This recipe stores policy and instructions related to project setup and scaffolding decisions.

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
