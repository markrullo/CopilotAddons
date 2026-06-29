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
- Do not create new work items or absorb newly discovered scope unless the user explicitly asks. Report blockers, risks, and follow-up work back to ADO instead.

## Process

1. Verify the ADO organization, project, and any available instructions before coding.
2. Load the supplied work item or work items from ADO.
3. If a higher-level item was supplied, traverse downward through the hierarchy, list the discovered child work items, and confirm that this is the intended scope before making code changes.
4. Build the execution order from dependency links. Only start items whose prerequisites are complete.
5. For each executable work item:
   - Move it to the appropriate active or in-progress state.
   - Read the requirements and linked context carefully.
   - Implement the work and validate it for that item's scope.
   - Rubber-duck the implementation for that item before closing it out.
   - Update the work item with a summary of the completed work, any issues encountered, and any follow-up notes.
   - Link the commit and/or PR.
   - Commit once that work item is complete.
6. If a work item cannot be completed, update ADO with the blocker and stop rather than committing partial work for that item.

## Output

- Clear status updates written back to each work item
- One commit per completed work item
- Explicit blocker and follow-up notes when work cannot continue
