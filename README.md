# Unity MCP UI Layout

Reusable Unity UI workflow rules for `unity-mcp`, packaged first as a Codex skill and then adapted for other LLM platforms.

The repository is built around one core idea: when an LLM creates Unity UI from a mockup, screenshot, or target resolution, it should work from anchors, parent containers, scaling rules, and verification loops instead of raw pixel placement.

## Default Platform

The default platform is `Codex`.

The canonical skill lives in:

- [`unity-mcp-ui-layout/`](./unity-mcp-ui-layout)

Platform-specific adapters live in:

- [`Platform/`](./Platform)

## What This Helps With

- image-to-layout translation
- UGUI anchors and `CanvasScaler`
- HUD, inventory, popup, and mobile safe-area layout rules
- screenshot verification loops
- safer `unity-mcp` prompting across different LLM products

## Repository Structure

```text
unity-mcp-ui-layout/
  SKILL.md
  agents/
  references/

Platform/
  README.md
  Codex/
    README.md
  Google-Antigravity/
    README.md
    SYSTEM_PROMPT.md
  Claude-Artifacts/
    README.md
    ARTIFACT_PROMPT.md
```

## Platform Notes

### Codex

Use the skill folder directly by copying `unity-mcp-ui-layout` into your Codex skills directory.

### Google Antigravity

Use the prompt package in `Platform/Google-Antigravity/` as the base instruction set for an Antigravity workspace or custom skill-like setup that has access to Unity through MCP or an equivalent bridge.

### Claude Artifacts

Use the prompt package in `Platform/Claude-Artifacts/` as the base instruction for a Claude project or artifact workflow that is connected to Unity tooling.

## Install For Codex

### Windows

```powershell
Copy-Item -Recurse -Force .\unity-mcp-ui-layout $HOME\.codex\skills\
```

### macOS / Linux

```bash
cp -R ./unity-mcp-ui-layout ~/.codex/skills/
```

## Example Request

```text
Use $unity-mcp-ui-layout to build a 1920x1080 UGUI HUD from the attached layout image.
Translate the composition into anchors, parent containers, and CanvasScaler rules.
Verify the result with screenshots instead of relying on raw pixel placement.
```

## Platform Examples

### Codex

```text
Use $unity-mcp-ui-layout to repair the current inventory layout in UGUI.
Preserve the style, fix slot spacing and scaling drift, and verify at 1920x1080 plus one narrower aspect ratio.
```

### Google Antigravity

```text
Build this Unity HUD from the attached mockup at 1920x1080.
Treat the image as a composition reference, create parent regions first, then verify with screenshots.
```

### Claude Artifacts

```text
Using the attached mockup, help me build a 1920x1080 Unity HUD in UGUI.
Please work in an artifact-style loop with sections for Plan, Current Change, Verification, and Next Step.
```

## Notes

- The Codex skill is the source of truth.
- The platform folders adapt the same workflow for other LLM services.
- Real project usage should drive future refinements.
