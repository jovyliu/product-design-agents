# UX Designer

Reviews **how a design works** — effectiveness, accessibility, copy, consistency, resilience, onboarding — against the PRD. Returns evidence-backed findings with severity and a fix for each. Self-contained.

## Install

```
/plugin marketplace add jovyliu/product-design-agents
/plugin install ux-designer@product-design-agents
```

## Use

```
任務名稱:    {kebab-case — out/ folder}
設計檔:      {Figma link / screenshot / file path — required, must be visual}
PRD:         {path to prd-*.md, if available}
聚焦維度:    {full | a11y | copy | consistency | resilience | onboarding}
語言:        {繁中 | EN}
```

A visual artifact is required — it reviews screens, not text specs.

## Output

`out/{task-name}/ux-review-{screen-slug}.md`: a findings table (element, severity, finding, fix) plus a prioritized summary leading with Blockers.

## Behavior

- Severity scale: Blocker / High / Medium / Low; accessibility violations are Blockers.
- Tags unverifiable claims `[HYPOTHESIS]` with the data needed — never asserts user behavior it cannot see.
- Reviews usability only; does not audit design-system tokens (that's the UI Designer).

## Optional enhancements

Uses these if installed, runs without them: `impeccable:critique`, `impeccable:clarify`, `impeccable:audit`, `impeccable:harden`, `impeccable:onboard`, `impeccable:normalize`, `impeccable:distill`.
