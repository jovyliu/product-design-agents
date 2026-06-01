# Product Design Agents

Four standalone product-design agents for Claude Code, published as one marketplace. **Install only the ones you need** — each works on its own, with its full methodology built in. No agent depends on another, and none requires extra skills to function.

| Plugin | Job | Model |
|--------|-----|-------|
| `product-manager` | Raw idea → discovery → validation → user stories → PRD | opus |
| `ux-designer` | Review usability, a11y, copy, consistency, resilience against the PRD | opus |
| `ui-designer` | Generate designs, bind to a design system, polish, audit drift | opus |
| `qa-engineer` | PRD → test plan, regression scope, bug-report template | sonnet |

These cover a lean product squad: a PM who specs it, a UX Designer who checks it works, a UI Designer who makes it look right, and a QA Engineer who proves it holds.

## Install

Add the marketplace once, then install any subset:

```
/plugin marketplace add jovyliu/product-design-agents
/plugin install product-manager@product-design-agents
/plugin install ux-designer@product-design-agents
/plugin install ui-designer@product-design-agents
/plugin install qa-engineer@product-design-agents
```

Replace `jovyliu/product-design-agents` with your actual GitHub `owner/repo` after you push.

## How they chain (optional)

There is no coordinator — you drive. Each agent reads the prior deliverable from `out/{task-name}/`, so a full pass is just:

```
product-manager  → out/{task}/prd-*.md
       ↓ (UI and UX read the PRD; they can run in parallel)
ui-designer      → out/{task}/design/ + ds-audit-*.md
ux-designer      → out/{task}/ux-review-*.md
       ↓
qa-engineer      → out/{task}/test-plan-*.md
```

Use one agent alone whenever that is all you need.

## The input template (paste this to any agent)

Filling more fields means fewer questions and fewer tokens spent. Leave a field blank only when you genuinely don't know it — blanks are the only thing an agent will ask about.

```
任務名稱:      {kebab-case — becomes the out/ folder name}
一句話描述:    {what the feature is}
目標用戶:      {who}
要解決的問題:  {pain / job-to-be-done}
商業目標:      {why now}
範圍-要做:     {in scope}
範圍-不做:     {explicitly out of scope}
已知約束:      {platform / design system / timeline / tech}
設計系統參考:  {tokens file / Figma library / component list — UI Designer needs this}
既有上游檔:    {paths to PRD / design / research already produced}
要的產出:      {prd | ux review | design+DS | test plan | 全部}
語言:          {繁中 | EN}
```

Each agent reads only the fields it needs and ignores the rest.

## Output

All deliverables land under `out/{task-name}/` at your project root, each with a YAML metadata header declaring its `upstream:` files. That is the read surface and the handoff between agents.

## Design notes

- **No coordinator, no process reviewer** — this is a hand-tuned personal toolkit, not an orchestrated team. You invoke each agent directly.
- **Rules are embedded in each agent**, not shipped as separate rule files, because Claude Code plugins contribute agents/skills/hooks but not project rules. Each agent therefore carries its own anti-sycophancy, writing-quality, and output conventions.
- **External skills are optional power-ups**, never hard dependencies. If you have `impeccable`, `pm-thinking-coach`, `qa-test-planner`, or the Figma MCP installed, the relevant agent will use them; if not, it runs its built-in methodology. Third-party skills are not redistributed here.

## License

Internal use.
