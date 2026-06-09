# Product Manager

Turns a raw idea into a validated PRD in one engagement: **discovery → direction validation → user stories → PRD**. Self-contained — no other plugin or skill required.

## Install

```
/plugin marketplace add jovyliu/product-design-agents
/plugin install product-manager@product-design-agents
```

## Use

Paste a design request. Fill what you know; blanks are the only thing it asks about.

```
任務名稱:      {kebab-case — out/ folder name}
一句話描述:    {what the feature is}
目標用戶:      {who}
要解決的問題:  {pain / job-to-be-done}
商業目標:      {why now}
範圍-要做:     {in scope}
範圍-不做:     {explicitly out of scope}
已知約束:      {platform / design system / timeline / tech}
既有上游檔:    {paths to any prior brief / research}
要的產出:      {brief | validation | stories | prd | 全部}
語言:          {繁中 | EN}
```

## Output

One self-contained HTML: `out/{task-name}/{task-name}.html`. A sticky segmented control switches between Brief / Validation / Stories / PRD; only the moves you ran appear, PRD opens by default. No external dependencies — opens by double-click, renders offline. Ask for just one move and it adds that segment to the same file instead of redoing the rest.

## Behavior

- One decision question at a time; interim summary every 3-4 rounds.
- Takes evidence-backed positions; one verdict (PROCEED / PIVOT / STOP) at validation.
- Never fabricates market data or fills an unmade decision — surfaces it under Open Decisions.

## Optional enhancements

Uses these if installed, runs without them: `pm-thinking-coach`, `idea-validator`, `feature-story-writer`, `story-to-prd`.
