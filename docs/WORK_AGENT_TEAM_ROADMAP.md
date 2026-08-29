# Work Agent Team Roadmap

- Status: proposed fork extension
- Last updated: 2026-08-29
- Audience: skill authors, evaluators, and new contributors

## Plain-language purpose

The Work Agent Team is a set of role-specific instruction packages. Its next stage should make hand-offs, safety boundaries, and evaluation results as clear as each individual role. This document describes a fork-local direction; it does not claim to be part of the upstream Anthropic roadmap.

## Role contract

Every agent or skill should declare:

- the outcome it owns;
- inputs it may read and outputs it may create;
- actions it may never take;
- what evidence makes its result complete;
- when it must hand work back to a person or another role.

## Orchestration principles

1. Use the smallest number of roles needed for the outcome.
2. Pass conclusions, evidence, and explicit open questions—not an uncontrolled copy of private context.
3. Keep one authoritative artifact for each decision or plan.
4. A reviewer checks requirements and evidence; it does not silently redefine the request.
5. External writes, messages, or releases require the authorization appropriate to that action.

## Evaluation matrix

| Dimension | Question |
|---|---|
| Trigger accuracy | Did the correct role activate for the request? |
| Scope control | Did it avoid unrelated actions and private context? |
| Completeness | Are required outcomes and acceptance checks present? |
| Handoff quality | Can the next role act without guessing? |
| Evidence | Are facts separated from assumptions? |
| Efficiency | Did the workflow avoid duplicate roles and artifacts? |

Use synthetic examples for public evaluation. Never publish private vault content, credentials, employer material, or personal histories as test fixtures.

## Development sequence

### Now

- inventory the six roles using the role contract;
- define one canonical hand-off example;
- mark fork-specific behavior separately from upstream content.

### Next

- add small positive, negative, and ambiguous trigger tests;
- score single-role and multi-role workflows with the evaluation matrix;
- version shared output schemas.

### Later

- automate regression checks for skill changes;
- publish public-safe examples and contribution guidance;
- propose generally useful improvements upstream as small, attributable changes.

## Risks and open questions

- Overlapping descriptions can activate too many roles.
- Evaluation examples can accidentally encode one user's private workflow.
- Open question: which role pairing should be the first end-to-end benchmark?
