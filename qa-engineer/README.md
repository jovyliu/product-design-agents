# QA Engineer

Turns a PRD into a test plan anyone can execute: manual cases (happy / edge / negative), regression scope, environment matrix, and a bug-report template. Scope is functional coverage, not UX or visual critique. Self-contained.

## Install

```
/plugin marketplace add jovyliu/product-design-agents
/plugin install qa-engineer@product-design-agents
```

## Use

```
任務名稱:    {kebab-case — out/ folder}
PRD:         {path to prd-*.md — required}
平台約束:    {browsers / devices / OS versions in scope}
語言:        {繁中 | EN}
```

A PRD with acceptance criteria is required — there must be something to verify against.

## Output

`out/{task-name}/test-plan-{feature-slug}.md`: coverage matrix, test cases (ID, type, precondition, steps, expected), regression scope, environment matrix, bug-report template, and a Coverage Gaps section.

## Behavior

- At least one case per acceptance criterion; happy + edge + negative per primary journey.
- Flags untestable criteria and proposes measurable rewrites instead of guessing.
- Lists ambiguous criteria under Coverage Gaps rather than silently picking an interpretation.

## Optional enhancements

Uses these if installed, runs without them: `qa-test-planner`, and the **Figma MCP** to validate cases against the design.
