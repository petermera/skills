# Skill Design and Testing Principles

A skill is a small, reusable instruction package that helps Claude perform one kind of work consistently.

## Standard shape

```text
skill-name/
├── SKILL.md        # Required: purpose, trigger, workflow, and guardrails
├── scripts/        # Optional: deterministic or repeated operations
├── references/     # Optional: detailed knowledge loaded only when needed
└── assets/         # Optional: templates and reusable output material
```

Keep `SKILL.md` focused. Put large examples and background material in `references/` so the model can load them progressively.

## Write a precise trigger

The description should say:

- what outcome the skill produces;
- what inputs it expects;
- when it should be used;
- when a different skill or tool is the better route.

Avoid broad triggers such as “helps with documents.” Prefer a narrow job such as “creates a weekly product-metrics review from a supplied table.”

## Separate judgment from mechanics

Use instructions for decisions that require context. Use scripts for deterministic transformations, validation, or repeated file operations. A script should have clear inputs, outputs, failure messages, and no embedded secrets.

## Design for composition

A skill should do one coherent job and state its boundaries. If a workflow needs several specialties, compose a few narrow skills through an orchestrator rather than growing one oversized skill.

When a task needs current external data or actions in another service, pair the skill with an MCP connector. The skill explains the method; the connector provides the live capability.

## Test before publishing

Test at least:

1. an ordinary request that should trigger the skill;
2. a request that should not trigger it;
3. missing or malformed input;
4. a realistic end-to-end task;
5. any safety boundary involving secrets, private data, or external writes.

Review both the final artifact and the process: correct files, correct tools, no leaked context, and understandable errors. Improve the trigger and workflow after observing failures.

## Contributor checklist

- `SKILL.md` exists and is readable without hidden context.
- The description is narrow and outcome-oriented.
- Required inputs and stopping conditions are explicit.
- Large knowledge is routed through `references/`.
- Repeated mechanics use tested scripts where useful.
- Examples contain no private company, customer, health, or credential data.
- The skill works alone and alongside related skills.
