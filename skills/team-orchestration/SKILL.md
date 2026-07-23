---
name: team-orchestration
description: Coordinate a reusable Claude work team made of a lead and specialist agents for product development, quality review, documents, data, visual design, communications, and skill maintenance. Use when a request has multiple independent deliverables, needs parallel specialist work, asks to create an agent team, or requires routing work to the correct specialist agent and skills.
---

# Team Orchestration

Coordinate work through `work-lead`. Keep agent count proportional to the task and prefer one agent for small, sequential requests.

## Route Work

Read [references/agent-map.yaml](references/agent-map.yaml) before creating assignments. Select agents by the requested deliverables, not merely by keywords.

- Route Claude applications, MCP integrations, frontends, and interactive artifacts to `product-builder`.
- Route independent functional checks and browser testing to `quality-reviewer`.
- Route Word, PDF, PowerPoint, and spreadsheet deliverables to `document-producer`.
- Route brand systems, static visuals, generative art, and animated GIFs to `creative-director`.
- Route new or revised skills and agent definitions to `skill-maintainer`.
- Keep planning, task ownership, synthesis, and user communication with `work-lead`.

## Coordinate the Team

1. Define the final deliverables and acceptance checks.
2. Split only work that can proceed independently.
3. Assign every file or artifact to exactly one owner.
4. Tell each agent which skills to use when spawning an agent-team teammate. Agent-team teammates do not inherit the `skills` field from a reused subagent definition.
5. Run independent assignments in parallel when useful.
6. Send implementation work to `quality-reviewer` when it can be tested independently.
7. Return failures to the original owner with concrete evidence.
8. Wait for required agents, synthesize their results, and report validation and remaining risks.

## Guardrails

- Do not create a team for a quick single-output task.
- Do not let agents edit the same file concurrently.
- Do not let a reviewer silently repair the implementation it is reviewing; return defects to the owner unless explicitly authorized.
- Do not load every skill into every agent.
- Require agents to report files changed, checks run, unresolved risks, and decisions needed.
- Keep destructive actions, external publication, credential use, and production changes behind explicit approval.

## Start an Agent Team

Ask Claude Code to create named teammates using the definitions in the plugin's `agents/` directory. Include the relevant skill list from the agent map in each spawn instruction. Create a shared task list with clear dependencies and exclusive ownership.
