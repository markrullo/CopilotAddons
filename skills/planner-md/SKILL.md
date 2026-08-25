---
name: planner-md
description: This skill is used to plan out a project or task by breaking it down into smaller, manageable steps. It can help you organize your thoughts and create a clear roadmap for completing your project.
---

# How to use and Model to use
Spin off a subagent to perform this work. Ideally use GPT-5.6 Luna for the subagent.

# Planning Skill
You create plans. You do NOT write code.

# When to use
This is to build on `/grilling` to create a plan and have it broken down into the structure Feature -> User Story -> Task . This is to facilitate another skill that will write this plan after it's reviewed by a human, to Azure Devops(ADO) as work items.

## Goals
- Create a plan using the `/grilling` skill to develop a plan for a project or task.
- The plan should be broken down into smaller, manageable steps, and should include a clear roadmap for completing the project.
- This skill will make a markdown file with the plan.  This plan will be broken down so in the future it'll be easy to take this output and bring it into ADO, prefer Feature -> User Story -> Task Structure, and make sure User Stories are broken down into executable Tasks.
- Ensure that all necessary information is gathered before proceeding with the plan.

## Process
- Once there is consensus on the plan, before writing the markdown file, ensure to rubber-duck the whole plan to ensure that it is complete and meets the requirements. 
- Upon successful rubber-ducking, proceed to the output instructions.

## Output
Create work items in a markdown file in `/plans`. Ensure that items are created with proper dependencies clearly outlined so implementation can be done in the correct order.  Do not create the plan if there is any ambiguity or missing information.  Ensure that the plan is clearly written in a Feature -> User Story -> Task structure.  This will make it easy to take this output and bring it into ADO, and make sure User Stories are broken down into executable Tasks.  Ensure all dependencies are clearly outlined so implementation can be done in the correct order.  If there is any ambiguity or missing information, do not create the plan.  
