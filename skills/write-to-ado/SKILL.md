---
name: write-to-ado
description: This skill is used to ingest a plan in a markdown file and create work items in Azure DevOps(ADO) as work items.
---

# Write to ADO Skill
Your purpose is to ingest a plan from a markdown file and create work items in Azure DevOps(ADO) as work items.  You do **not** create plans or invent backlog structure.  You are the implementation skill for Azure DevOps-backed work.  You also do **not** implement work items.  You are only responsible for creating work items in ADO from a markdown file that has been created by the `/planner-md` skill.

# When to use
After using the `/planner-md` skill to create a plan in a markdown file, use this skill to create work items in Azure DevOps(ADO) as work items.

## Goals
- Read the plan from a markdown file and create work items in Azure DevOps(ADO) as work items.
- The plan should already be broken down into clear work items.  If this is not apparent, ask the user to clarify the plan before proceeding.
- When persisting the plan to ADO, prefer Feature -> User Story -> Task, and make sure User Stories are broken down into executable Tasks because the next step is to use the `/coder-ado`  skill to implement Tasks and Bugs, not undecomposed higher-level items.  Recording dependencies in ADO is important to ensure that the `/coder-ado` skill can implement work items in the correct order.

## Process
- Before creating work items, ensure the required information is available.  If not, provide a warning to the user that they should create a global file that outlines their preferences, typically `copilot-instructions.md`.  Project specific instructions can be put in the project under `\docs\agents\issue-tracker.md` . The `/setup-verification-ado` skill can be used to verify the required information is available.
- Read the markdown file and parse the plan into work items.
- Ensure the plan is clear and unambiguous. If there are any ambiguities or missing information, provide a warning to the user, provide guidance on what the ambiguities are, and stop.  Do not create work items if there is any ambiguity or missing information.
- Ensure all dependencies are clearly recorded in ADO as parent/child links or dependency links. This will clearly outline the order of implementation for the `/coder-ado` skill. 

## Output
Create work items in ADO preferring the MCP server. Ensure that items are created with proper dependencies clearly outlined so implementation can be done in the correct order. If there are any issues with creating work items, provide a warning to the user and stop.  Do not create work items if there is any ambiguity or missing information.

### Required information
- ADO organization URL
- ADO project name
