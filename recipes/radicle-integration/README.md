# Radicle Integration Report

**Date:** 2026-05-16
**Author:** Nebula (automated)
**Target:** Legacy Computer (Sprite) -- Nebula Cloud Sandbox

---

## 1. Executive Summary

Radicle is a peer-to-peer, local-first code collaboration stack built on Git. Unlike GitHub, there are no centralized servers, API rate limits, or PATs. All social artifacts -- issues, patches (PRs), comments, and reviews -- are stored as Git commit objects and synced via a gossip protocol.

This report covers the current Radicle installation on Sprite, the CLI workflow, and a practical integration path for Nebula agent workflows.

---

## 2. Current State on Sprite

| Component | Status | Details |
|-----------|--------|---------|
| `radicle-node` | Installed | v1.8.0 (edde15d) at `/home/sprite/.radicle/bin/radicle-node` |
| `rad` CLI | Installed | Available at `/home/sprite/.radicle/bin/rad` |
| `git-remote-rad` | Installed | Git remote helper for `rad://` URLs |
| Radicle identity | **Not initialized** | No `~/.radicle/radicle.json` config found |
| Node running | **Not started** | Node must be started before any P2P operations |
| SSH config | Present | GitHub SSH key at `~/.ssh/id_ed25519` |

**Gap:** The toolchain is installed but no Radicle identity has been created and the node is not running. Section 5 covers initialization steps.

---

## 3. Architecture Overview

### How Radicle Works

1. **Identity** -- Each user has a cryptographic identity (a DID based on Ed25519 keys). Your identity is your public key. No sign-up, no email, no OAuth.
2. **Projects** -- A Radicle project is a Git repo with an identity payload stored under `refs/rad/id`. The project ID is derived from the initial commit's hash.
3. **Social Objects (COBs)** -- Issues, patches, and comments are stored as **Collaborative Objects** (COBs) in the Git object database. They are regular Git commits with a specific schema.
4. **Sync** -- A background node process gossips with seed nodes and peers to exchange Git objects. No push/pull to a central server.
5. **Seeds** -- Public seed nodes (e.g., `iris.radicle.xyz`, `rosa.radicle.xyz`) provide discovery and availability. You can also run your own seed.

### Key Differences from GitHub

| Feature | GitHub | Radicle |
|---------|--------|---------|
| Identity | Email + PAT | Ed25519 keypair (DID) |
| Issues | API-backed | Git COB objects |
| PRs | API-backed | Patches (Git refs) |
| Comments | API-backed | Git COB objects |
| Auth | PAT / OAuth | SSH key (same as Git) |
| Rate limits | Yes (5000/hr) | **None** -- local Git ops |
| Offline work | Limited | Full read/write, sync later |
| Hosting | Microsoft cloud | P2P gossip + seeds |

---

## 4. CLI Command Reference

### Identity & Auth

```bash
# Initialize your Radicle identity (one-time)
rad init

# Show your identity (DID + Node ID)
rad self

# Authenticate with a profile
rad auth
```

### Repository Workflow

```bash
# Initialize a new Radicle project
rad init --name "my-project" --description "A project"

# Clone an existing Radicle project
rad clone rad://<project-id>

# Publish to the network
rad publish

# Sync with peers/seeds
rad sync

# Check what's changed
rad inspect
```

### Issues (replace GitHub Issues)

```bash
# Open an issue
rad issue open --title "Bug: flux capacitor broken" --description "Details here"

# List issues
rad issue list

# Show issue details
rad issue show <issue-id>

# Comment on an issue
rad issue comment <issue-id> --message "I can reproduce this"

# Close an issue
rad issue close <issue-id>
```

### Patches (replace GitHub PRs)

```bash
# Create a patch from a branch
git checkout -b fix-flux-capacitor
# ... make commits ...
git push rad -o patch.message="Fix flux capacitor" HEAD:refs/patches

# List patches
rad patch list

# Show patch details
rad patch show <patch-id>

# Review a patch
rad patch review <patch-id> --accept  # or --reject

# Update a patch (push new commits)
git push rad -f HEAD:refs/patches/<patch-id>
```

### Node Management

```bash
# Start the node (runs in background)
rad node start

# Check node status (peers, sync state)
rad node status

# Connect to a specific seed
rad node connect <node-id>@iris.radicle.xyz:8776

# Stop the node
rad node stop

# Show node stats
rad node stats
```

### Following & Discovery

```bash
# Follow a peer (to see their projects)
rad follow <node-id>

# List followed peers
rad follow list

# List known projects
rad ls

# Seed a project (host it for others)
rad seed <project-id>
```

---

## 5. Initialization Steps for Sprite

Run these commands on Legacy Computer (Sprite) to get Radicle fully operational:

```bash
# Step 1: Initialize identity
rad init

# Step 2: Start the node
rad node start

# Step 3: Connect to default seeds
rad node connect z6Mkmqogy2qEM2ummccUthFEaaHvyYmYBYh3dbe9W4ebScxo@iris.radicle.xyz:8776

# Step 4: Verify connectivity
rad node status

# Step 5: Set up auto-start (optional)
# Add to crontab or systemd user service
```

---

## 6. Integration with Nebula Agent Workflows

### Why Radicle for Agents

- **No rate limits** -- Agents can create issues, patches, and comments without API quotas
- **Offline-first** -- Agents can work locally and sync when connectivity is available
- **Git-native** -- All operations are standard Git commands, no REST API wrappers needed
- **Deterministic** -- COB IDs are content-addressed, making idempotent operations trivial

### Recommended Workflow

1. **Code review agent** -- Clone Radicle repos, create patches for fixes, open issues for bugs found
2. **Project tracker agent** -- Monitor issue state across Radicle projects, report status
3. **Documentation agent** -- Track docs as patches, review via Radicle's patch review system

### Example: Agent Creates a Patch

```bash
# Agent workflow for submitting a code fix
cd /home/sprite/projects/my-project
git checkout -b agent-fix-$(date +%s)
# ... agent makes changes ...
git add -A
git commit -m "Fix: resolve issue #<id>"
git push rad -o patch.message="Agent fix for issue #<id>" HEAD:refs/patches
```

---

## 7. Seed Node Reference

| Seed | Address | Notes |
|------|---------|-------|
| Iris | `iris.radicle.xyz:8776` | Primary seed (replaces seed.radicle.garden) |
| Rosa | `rosa.radicle.xyz:8776` | Secondary seed (replaces ash.radicle.garden) |

**Migration note:** Old seed DNS names (`seed.radicle.garden`, `ash.radicle.garden`) still work but show warnings. Use the new `radicle.xyz` names.

---

## 8. Version History (Recent)

| Version | Date | Key Changes |
|---------|------|-------------|
| 1.2.1 | 2025-07-17 | Seed DNS migration, patch review improvements, comment templates |
| 1.3.0 | 2025-08-12 | Canonical reference rules, new `radicle-protocol` crate |
| 1.4.0 | 2025-09-03 | Canonical reference fixes, panic fixes, improved Git push behavior |
| 1.8.0 | Current | Latest stable on Sprite |

---

## 9. Resources

- **User Guide:** https://docs.radicle.xyz/guides/user
- **CLI Reference:** https://docs.rs/crate/radicle-cli/latest
- **Blog/Changelog:** https://radicle.dev
- **Community:** Zulip chat (linked from radicle.dev)

---

*Report generated by Nebula. Radicle node status verified on Legacy Computer (Sprite) sandbox.*