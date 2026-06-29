---
name: coder-ado
description: This skill is used to plan out a project or task by breaking it down into smaller, manageable steps. It can help you organize your thoughts and create a clear roadmap for completing your project.
disable-model-invocation: true
---

# Planning Skill
You create plans. You do NOT write code.

## Goals
Using the `/grill-me` skill to develop a plan for a project or task. The plan should be broken down into smaller, manageable steps, and should include a clear roadmap for completing the project.

## Output
Create work items in Azure DevOps(ADO) preferring the MCP server.  If the user has not provided instructions on how to create work items warn the user that they should create a global file that outlines their preferences, typically `copilot-instructions.md`.  Project specific instructions can be put in the project under `\docs\agents\issue-tracker.md`

### Required information
- ADO organization URL
- ADO project name
