# UI Reference Researcher

Maps each **PRD section to its user story** and finds **matching real-world UI references on Mobbin**, delivered as an annotated comparison doc with embedded screenshots. Researches and documents — does not redesign. Self-contained.

## Install

```
/plugin marketplace add jovyliu/product-design-agents
/plugin install ui-reference-researcher@product-design-agents
```

Strongly recommended: connect the Mobbin MCP so the agent can fetch real, citable screenshots.

```
claude mcp add mobbin --transport http https://api.mobbin.com/mcp
# then in a session: /mcp → mobbin → Authenticate → restart the session
```

## Use

```
任務名稱:        {kebab-case — out/ folder}
頁面/流程來源:   {path to mockup html / figma export, or a section list}
PRD / Stories:   {path to prd-*.md or GO-*.html — source of user stories / FRs}
平台:            {web | ios}
設計系統參考:    {tokens file / brand colors — optional, for the implementation note}
語言:            {繁中 | EN}
```

If `PRD / Stories` is missing it returns `NEEDS_INPUT`. If the page source is missing it derives sections from the PRD's User Journey.

## Output

- Comparison doc: `out/{task-name}/{task-name}-ui-references.html`
- Screenshots: `out/{task-name}/ui-ref-img/*.webp` (relative paths — the doc is portable and works offline)

Per-section card = heading + story badges + intent + a row of reference cards (screenshot, app name linking to its `mobbin_url`, pattern label, "why it fits", primary/alt tag) + a "借用" line. Ends with a one-page summary table.

## Behavior

- Every reference traces to a section; every section to a story/FR. A section with no story is flagged, not guessed.
- References chosen by the story's communication purpose, not aesthetics. Style is open unless constrained.
- One primary + one or two alternates per section, with a reason the primary wins.
- Screenshots are mandatory and downloaded locally; each also cites its Mobbin URL.
- Explicit invocation only — call it when you want UI references / pattern benchmarking.

## Optional enhancements

- **Mobbin MCP** — the source of real screenshots (`search_screens`, `search_flows`). Degrades to named-app + search-keyword recommendations if absent, never fabricated shots.
- **UI Designer agent** — downstream consumer for token-true implementation.
- **product-manager agent** — produces the PRD/stories this agent reads.
