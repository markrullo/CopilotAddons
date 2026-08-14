---
name: setup-verification-ado
description: This skill isn't directly invoked by the user. It is used to set up the environment and provide context for other skills.
disable-model-invocation: true
---

# Setup Verification ADO Skill
This skill doesn't code or plan. It is used to set up the environment and provide context for other skills. It ensures that the necessary instructions are already available either at the global level, project level, or both.

## Goals

-Insure that the user has provided instructions for the skill to follow.  If not, provide a warning to the user that they should create a global file that outlines their preferences, typically `copilot-instructions.md`.  Project specific instructions can be put in the project under `\docs\agents\issue-tracker.md`
-Required pieces of information:
  - Azure Devops (ADO) organization URL
  - ADO project name
  - Required setup of which work items to use.