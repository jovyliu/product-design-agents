# UI Designer

Owns **how the product looks and how it connects to the design system**: generate screens, apply a DS to drafts, polish the visual craft, and audit for drift. Self-contained.

## Install

```
/plugin marketplace add jovyliu/product-design-agents
/plugin install ui-designer@product-design-agents
```

## Use

```
任務名稱:        {kebab-case — out/ folder}
工作類型:        {generate | apply | polish | audit}
PRD / 需求:      {path to prd-*.md or a screen description}
設計檔:          {path/link to existing draft — required for apply/polish/audit}
設計系統參考:    {tokens file / Figma library URL / component list — required}
主題/品牌:       {theme name if the DS has multiple, e.g. light/dark}
語言:            {繁中 | EN}
```

If `設計系統參考` is blank, it looks for `product-context.yaml` and `ds-guide.md` at the project root.

## Output

Design artifacts in `out/{task-name}/design/`; audit report `out/{task-name}/ds-audit-{screen-slug}.md` with a change log, findings table, and a one-line verdict (CLEAN / EXCEPTIONS DOCUMENTED / OPEN FINDINGS).

## Behavior

- Token binding over hardcoded values; component reuse over local redraw.
- No screen ships without a clean audit or documented exceptions.
- Flags no-match elements with a promotion proposal instead of forcing a wrong token.

## Optional enhancements

Uses these if installed, runs without them: `apply-design-system`, `audit-design-system`, `fix-design-system-finding`, `impeccable:polish` / `bolder` / `quieter` / `colorize` / `delight`, and the **Figma MCP** for direct read/write in Figma.
