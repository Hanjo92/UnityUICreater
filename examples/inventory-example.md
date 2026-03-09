# Inventory Example

## Scenario

The user wants to create or repair a slot-based inventory panel in UGUI without manually placing each slot.

## Recommended Prompt

```text
Use $unity-mcp-ui-layout to build this as a UGUI inventory panel.
Create the main panel first, then split it into navigation, grid, detail panel, and bottom actions.
Use layout groups for repeated slots instead of manual placement.
Preserve the current visual style if assets already exist, and verify that the detail panel does not overlap the list at narrower widths.
```

## Expected Working Style

1. Create or inspect the main panel
2. Separate structural regions
3. Use layout groups for repeated slot placement
4. Verify spacing, overlap, and text behavior

## Useful References

- `unity-mcp-ui-layout/references/mcp-call-recipes.md`
- `unity-mcp-ui-layout/references/ugui-inventory.md`
- `unity-mcp-ui-layout/references/common-failures.md`
