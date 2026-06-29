# CopilotAddons

I'm trying to refine a workflow that first does planning and stores the plans in Azure DevOps (ADO).  Then the coder skill will grab the ADO tasks, work on them, then update progress so the team can see what's going on.  I've encorporated the use of grill-me developed by  (Matt Pocock) [https://github.com/mattpocock/skills]

[![skills.sh](https://skills.sh/b/markrullo/CopilotAddons)](https://skills.sh/markrullo/CopilotAddons)

`/setup-verification-ado` - this aims to verify the setup to ensure global and project instructions have already been provided.

`/planner-ado` - aims to use the grill-me skill with the added instruction of persisting the plan in ADO with the setup already provided by your config.

`coder-ado` - aims to be given a work item number to receive instructions from, perform the work, ask for anything missing instead of making that up.  Then write any progress back to the task.



## General setup

These are some general global instructions that I have setup:

``` md

## Output Style

- Prefer concise responses
- Use bullet points or step-based format
- Summarize multiple options before details
- Stop after logical step when performing multi-step tasks


## Work Items (Azure DevOps)

- Always confirm organization/project if not known
- Store confirmed values in \docs\agents\issue-tracker.md

### Creation Rules
- Prefer: Feature → User Stories → Tasks
- Bugs should be created as Bug work items
- Link work items appropriately

### Quality Rules
- Title: concise and descriptive
- Description: must include:
  - context
  - expected outcome
  - references (links, screenshots, work items)

### Completion Rules
- Update status
- Add comments summarizing work
- Link PRs / commits
- For bugs: include resolution details and follow-ups


## Guardrails

- Do NOT assume missing context — ask clarifying questions
- Do NOT generate code in planning mode
- Do NOT invent Azure DevOps structure — confirm when unsure
```