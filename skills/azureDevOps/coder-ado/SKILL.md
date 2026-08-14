---
name: coder-ado
description: Implements Azure DevOps work items in dependency order, updates ADO as it works, and commits each completed item.
disable-model-invocation: true
---

# Coding Skill

You are the implementation skill for Azure DevOps-backed work. You do **not** create plans or invent backlog structure.

## When to use

Use this skill when the user wants existing Azure DevOps work items implemented.

## Required inputs

- A seed work item ID or a small explicit set of work item IDs
- Confirmed Azure DevOps organization and project
- Available repo or project instructions, such as `\docs\agents\issue-tracker.md`, when they exist

If required setup is missing or inconsistent, stop and ask instead of guessing.

## Goals

- Implement **executable work items** only.
- Bugs are usually executable as-is.
- Higher-level items such as Features and User Stories must be decomposed into child Tasks before coding begins.
- If a Feature or User Story is supplied, discover the child work items, list the discovered scope, and confirm with the user before starting implementation.
- Use parent/child links to discover scope and dependency links to determine execution order.
- Ignore generic "related" links unless the user explicitly asks to include them.
- Ask for missing requirements instead of inventing them.
- Prefer the ADO MCP server for reading and writing work items, comments, links, and related metadata.
- Do not create new work items or absorb newly discovered scope unless the user explicitly asks. Report blockers, risks, and follow-up work back to the user and ADO instead.


## Branching & Commit Workflow

  ### Single Feature Branch Workflow  
      For each feature, create exactly one feature branch before beginning any development work. The branch name must include the feature identifier and a short descriptive slug 
      (e.g., 1) feature/F123-user-permissions. This branch represents the entire feature and remains the sole branch for all related development activity.

  ### Task-Level Commits  
      All tasks belonging to the feature must commit to this same feature branch. Each commit must reference: the task ID being addressed, and the feature the task belongs to. Ensure that commit messages are clear, concise, and descriptive of the work completed.  Update the ADO task with the commit reference and any relevant notes. Commits must be pushed to the feature branch as work progresses. No additional branches may be created for individual tasks.

  ### Main Branch Protection
      No commits may be made directly to main under any circumstances. All work must flow through the feature branch and later be merged via a pull request.

## Process

1. Verify the ADO organization, project, and any available instructions before coding.
2. Load the supplied work item or work items from ADO.
3. If a higher-level item was supplied, traverse downward through the hierarchy, list the discovered child work items, and confirm that this is the intended scope before making code changes.
4. Build the execution order from dependency links. Only start items whose prerequisites are complete.
5. For each executable work item:
   - Move it to the appropriate active or in-progress state.
   - Read the requirements and linked context carefully.
   - Implement the work and validate it for that item's scope.   
   - Update the work item with a summary of the completed work, any issues encountered, and any follow-up notes.
   - Link the commit and/or PR.
   - Commit once that work item is complete.
6. If a work item cannot be completed, update ADO with the blocker and stop rather than committing partial work for that item.


## Output

- Clear status updates written back to each work item
- One commit per completed work item
- Explicit blocker and follow-up notes when work cannot continue
