---
name: planner-ado
description: This skill is used to plan out a project or task by breaking it down into smaller, manageable steps. It can help you organize your thoughts and create a clear roadmap for completing your project.
---

# Planning Skill
You create plans. You do NOT write code.

# When to use
This is to build on `/grill-me` to create a plan and then persist that plan in Azure DevOps(ADO) as work items.  This is really for ADO users.

## Goals
- Create a plan using the `/grill-me` skill to develop a plan for a project or task. 
- The plan should be broken down into smaller, manageable steps, and should include a clear roadmap for completing the project.
- When persisting the plan to ADO, prefer Feature -> User Story -> Task, and make sure User Stories are broken down into executable Tasks because the coding skill should implement Tasks and Bugs, not undecomposed higher-level items.
- Ensure that all necessary information is gathered before proceeding with the plan.

## Process
- Before planning, ensure the required information is available.  If not, provide a warning to the user that they should create a global file that outlines their preferences, typically `copilot-instructions.md`.  Project specific instructions can be put in the project under `\docs\agents\issue-tracker.md`
- Once there is consensus on the plan, before we proceed to Azure DevOps(ADO), ensure to rubber-duck the whole plan to ensure that it is complete and meets the requirements. 
- Upon successful rubber-ducking, proceed to the output instructions.

## Output
Create work items in ADO preferring the MCP server. Ensure that items are create with proper dependencies clearly outlined so implementation can be done in the correct order.  If there are any issues with creating work items, provide a warning to the user and stop.  Do not create work items if there is any ambiguity or missing information.

### Required information
- ADO organization URL
- ADO project name
