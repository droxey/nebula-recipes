# Airbnb Listing Package Workflow

This folder stores the reusable Nebula recipe and repo-ready documentation for Airbnb listing package work.

## What this captures
- account-wide Airbnb listing defaults already saved in Nebula memory
- a reusable task recipe for preparing listing photo packages
- a suggested repository structure for committing the workflow to git

## Suggested repo structure
```text
airbnb-listing-workflows/
  README.md
  recipes/
    airbnb-listing-package/
      TASK.md
      AGENTS.md
      templates/
        package-AGENTS.md
        delivery-checklist.md
```

## Recommended git usage
Commit durable workflow assets only:
- recipe documents
- local rules files such as `AGENTS.md`
- templates and checklists
- scripts if you later automate parts of the packaging process

Avoid committing large generated zips or raw listing photo exports unless the repo is explicitly meant to store media.

## How to use later
Ask Nebula to run or adapt the Airbnb listing package recipe for a new listing folder. If a listing has special requirements, keep the account-level defaults and add a listing-specific `AGENTS.md` beside the package.
