# Copilot Addon Skills

This context defines the roles of the ADO-oriented skills in this repository so each skill has a clear boundary and handoff.

## Language

**Planning Skill**:
A skill that turns a request into an ADO-backed plan and work-item structure without implementing the work itself.
_Avoid_: coding skill, executor

**Coding Skill**:
A skill that implements one or more existing ADO work items in dependency order and records progress back to ADO, with a commit after each completed item.
_Avoid_: planner, backlog shaper

**Executable Work Item**:
A work item with enough concrete scope to implement directly. In this context, Bugs are usually executable, while higher-level items such as User Stories should be decomposed into Tasks first.
_Avoid_: vague story, undecomposed feature

**Completed Work Item**:
A work item that has been implemented, locally validated for its scope, and updated in ADO with the outcome, making it eligible for its own commit.
_Avoid_: partial progress, blocked item

**Stateful Execution**:
Work-item handling that updates ADO state when implementation starts and again when it completes, along with a summary and commit or PR references.
_Avoid_: silent coding, comment-only tracking

**Scope Expansion**:
Any newly discovered work outside the currently requested items. In this context, the coding skill reports it back to ADO but does not create or absorb new scope unless explicitly directed.
_Avoid_: silent backlog growth, self-assigned extra work

**Downward Discovery**:
When given a higher-level work item such as a Feature or User Story, the coding skill may traverse downward to find the child work items that are actually executable, then confirm the discovered scope with the user before starting implementation.
_Avoid_: blind backlog traversal, unconfirmed expansion

**Hierarchy-Driven Discovery**:
Parent and child work-item relationships define which items belong in scope during downward discovery, while dependency links define the order in which executable items can be worked.
_Avoid_: related-link sprawl, ambiguous traversal

**Work Item Dependency Order**:
The explicit execution sequence derived from linked ADO work items so implementation follows the intended prerequisites and never depends on guessed ordering.
_Avoid_: guessed order, ad hoc sequence
