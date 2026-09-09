# Planned UI With Project Images

Use this walkthrough for issues #80 (sequential planning) and #79 (project images and image generation). The paths below are illustrative, not inspected project assets or execution evidence.

## Request

```text
이 시안으로 Unity 보상 팝업을 만들어줘. 구조는 같이 정하고 싶어.
```

## Expected Conversation and Execution

1. Inspect the selected UI owner, supplied design, and project assets. Suppose the owner is UGUI and the project has `Assets/UI/Common/PopupFrame.png` and `Assets/UI/Icons/Coin.png`, but no matching chest illustration. Preview the images before choosing them; a missing asset index does not skip this inspection.
2. Ask the first missing behavior question: "보상은 팝업이 열릴 때 이미 지급된 상태인가요, 아니면 받기 버튼을 눌러 지급하나요?" Do not create a claim button until that distinction is settled.
3. After the user answers "이미 지급됐고 확인만 하면 돼", propose `ModalLayer -> Dimmer + SafeAreaPopup -> Title + RewardRow + ConfirmButton`, with the repeated reward unit and scroll rule if needed. Confirm only unresolved composition choices; do not reopen the agreed reward behavior.
4. Verify that the agent has an available image-generation skill, read its instructions, and check its execution requirements. Only if that skill and its generation path are available, show the asset gap and ask: "프레임과 코인 이미지는 프로젝트 리소스를 쓰고, 없는 상자 그림은 시안 스타일의 임시 스프라이트로 생성할까요?"
5. After "응, 임시로 생성하고 그 구조로 진행해", record the design agreement and temporary-resource authorization. Build the agreed slices, reuse the project images, generate and inspect the chest art, import it as a sprite, and assign it to the chest `Image`. Keep the output and provenance in the task artifacts.
6. Verify actual image references, the main and alternate-size screenshots, text, and console. Report the chest as temporary, with any remaining user art review; successful import is separate evidence from visual acceptance.

See [ui-planning-workflow.md](../unity-mcp-ui-layout/references/ui-planning-workflow.md), [image-asset-workflow.md](../unity-mcp-ui-layout/references/image-asset-workflow.md), and [agent-runbook.md](../unity-mcp-ui-layout/references/agent-runbook.md).

## Boundary Scenarios for Review

These are expected behaviors to check when revising the skill, not recorded test passes.

| Scenario | Expected behavior |
| --- | --- |
| No mockup: "상점 UI를 같이 기획하자" | Inspect known requirements, ask about the next missing product choice, then propose regions and structure; no invented purchase flow. |
| Supplied mockup, matching project sprites, no asset index | Discover directly, preview and reuse matching sprites; no placeholder-first fallback. |
| User already approved the tree and requested generation; image-generation skill is available and usable | Generate the agreed missing icons and apply them without repeating planning or generation questions. |
| Image-generation skill available and usable, temporary images undecided | Ask about the named image gaps before generating temporary resources. |
| No image-generation skill, standalone image tool available | Skip the generation question and generation; reuse project assets or authorized placeholders. |
| No image-generation skill, user already requested generation | Prior authorization does not replace the skill prerequisite; report the unavailable skill and skip generation questions and execution. |
| Skill listed but its instructions cannot be read | Treat it as unavailable; do not ask about generation or call an image tool directly. |
| Generation declined, placeholders allowed | Keep existing images; use explicit provisional placeholders only for gaps. |
| Skill available but its execution path is unavailable or fails, final art required | Report the limitation and unfinished art scope; continue only independent agreed work. |
| User unavailable with major structure unresolved | Retain a proposed plan and open choices; do not build the unconfirmed screen. |
| Explicit layout-only preview | Preserve assigned assets and use authorized placeholders without adding image generation. |
| One-widget spacing repair | Inspect and fix within the existing contract; no new brainstorming or art workflow. |
| UI Toolkit owner with missing image | Keep visual-tree/UXML/USS ownership and use a resolved image/background asset; no Canvas fallback. |
| Held decorative raster candidate | Keep it a note; no node, crop, or generated replacement. |
