# Testing Project Scaffolding Policy

## Goal
Create or update a minimal test project scaffold with only the files required for the requested validation, ensure the project folder exists before scaffolding, and leave the resulting changes explicitly staged and ready for commit, with commit and push only when the repository and current branch are clearly safe to use.

## When to use
Use this recipe when validating project setup flows, smoke-testing a scaffold, or creating a minimal example project to verify tooling, build steps, or file layout without expanding the scope of changes.

## Desired final structure
1. Project folder exists
2. Minimal scaffold for the requested test case
3. Only required file edits
4. Exact changed files staged and commit-ready
5. Commit and push only if repo and branch state are clear

## Workflow
1. Confirm the target project path and create the project folder if it does not already exist.
2. Scaffold only the smallest viable project needed for the requested test.
3. Inspect the generated files and keep only what is required for the task.
4. Make the minimum necessary edits to satisfy the requested validation or fix.
5. Avoid unrelated cleanup, refactors, or optional enhancements.
6. Review the repository state before any git action.
7. Stage only the exact files that belong to the requested scaffold or required edits.
8. Leave the branch commit-ready after verifying the staged diff matches the requested scope.
9. Commit only if the repository is initialized, the current branch is clear and appropriate, and there is no ambiguity about where the change should land.
10. Push only if the target remote and branch are clearly intended and safe.

## Editing principles
- Create the target folder before scaffolding if it is missing.
- Prefer the smallest possible scaffold that still proves the requested behavior.
- Change only files required for the test or requested outcome.
- Do not add polish, refactors, or extra tooling unless directly required.
- Keep staged changes exact, reviewable, and ready for a clean commit.
- If repository or branch intent is unclear, stop after staging and report the state rather than guessing.

## Outputs
- New or updated minimal project scaffold in the requested folder
- Exact required files staged and ready for commit
- Commit and push only when repository and branch state are clearly safe
