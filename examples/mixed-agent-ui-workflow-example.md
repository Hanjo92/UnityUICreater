# Mixed-Agent UI Workflow

Use with [agent-capability-routing.md](../unity-mcp-ui-layout/references/agent-capability-routing.md). This is an illustrative assignment, not a statement about any provider's fixed capabilities or a recorded live test.

For a separate recorded execution, see the [2026-09-09 live validation](../docs/validation/2026-09-09-agent-capability-routing.md), including the initial routing ambiguity, correction, follow-up, and untested runtime paths.

## Request and Observed Session Capabilities

```text
이 시안으로 UI를 구현해줘. 여러 에이전트로 나눠 진행하고,
프로젝트 이미지를 먼저 쓰되 부족한 그림만 임시로 생성해줘.
```

After checking the actual sessions, suppose the coordinator records:

| Executor | Verified for this task | Missing or unverified |
| --- | --- | --- |
| coordinator | Task/decision access and orchestration | Vision, image-generation skill, live Unity access |
| visual-worker | Actual mockup/image input and interpretation | Generation skill, Unity mutation |
| code-worker | Shared source files and text/structured plan input | Vision, generation skill/tools, live Unity bridge |
| art-worker | Its own generation skill and text-to-image execution allowed by that skill | Vision, Unity bridge |
| unity-worker | Correct project/Editor, import/assignment/readback, screenshot capture | Vision, generation skill |

The runtime labels might be Orca/Paseo-managed sessions, Claude, OpenCode, or API workers; assignment depends on the checked row, never the label. Do not assume these participants exist or spawn this fixed team for every task.

## Assignment and Handoff

1. The visual worker opens the actual mockup and relevant project images, proposes the neutral layout tree and candidate ledger, and reports asset matches or gaps with source IDs, dimensions, and uncertainty. User decisions and candidate review are resolved under the existing workflow.
2. The coordinator gives the code worker the agreed tree, selected UI stack, reviewed asset IDs, source/normalized rects with coordinate conventions, required behavior, and writable paths. The code worker implements from this handoff without analyzing the raster or inventing unprovided measurements.
3. The art worker reads its own generation skill. It may generate the agreed missing image from the approved text brief because this example assumes its skill allows that. The initial request already authorized temporary generation, so no repeat question is needed. The coordinator's lack of a skill does not matter to this verified executor; a tool-only code worker would remain ineligible.
4. The art worker returns the candidate, prompt/source provenance, and `awaiting_visual_review`. The visual worker opens that exact output at its intended display size. Any rejection returns to the art worker with concrete feedback; an accepted provisional candidate still retains temporary status.
5. The Unity worker applies the reviewed image and scoped source changes, checks import/assignment and console state, and captures main and alternate-size screenshots. Mutations to the same live target are serialized; the code worker does not concurrently edit that target's files.
6. The screenshots and source revision reach the visual worker as actual images. The visual worker compares them against the agreed design and returns visual findings with artifact IDs. The coordinator reports those attributed findings separately from technical checks and remaining user art review.

## Boundary Scenarios for Review

Expected behaviors below are review cases, not recorded execution results.

| Scenario | Expected assignment or stop condition |
| --- | --- |
| Parent has vision/generation; child is a text-only API worker | Keep visual/generation roles with qualified executors; give child an approved text/structured implementation task. No inheritance assumption. |
| A vision model is selected but the API adapter omits image content | Vision is unverified for that artifact. Fix image delivery before assigning analysis or QA. |
| Child can read a PNG path or base64 string but cannot interpret images | Allow metadata/transfer work only; do not ask for raster layers, crop bounds, or visual matching. |
| Parent has generation skill; child has image tool only | The child cannot ask about generation or generate. Keep it with a qualified parent or another verified executor. |
| Coordinator lacks skill; verified generation worker has skill and execution path | Worker owns generation and any generation question; coordinator may relay that specific question once. |
| Coordinator asks a skill-less implementation child to forward a generation question | Child reports the capability gap internally. Only the qualified generation owner or designated coordinator presents the question; parent skill alone does not establish usable generation. |
| No executor has a generation skill | Skip generation questions and execution across the team; use project assets or authorized placeholders. |
| Generation worker lacks vision and its skill requires reference inspection | Do not assign that reference-based generation task; use an executor meeting the skill's requirements. |
| Generation succeeds but nobody can inspect the output | Retain an unreviewed candidate; do not select/apply it as reviewed art or report visual PASS. |
| All workers lack vision; a valid structured export and approved plan exist | Textual/structural work may proceed within scope; image comparison and visual QA remain pending. |
| All workers lack vision; the only source is an unanalyzed raster mockup | Hold raster-dependent planning and implementation; continue independent project inspection. |
| Unity operator captures screenshots but lacks vision | Return images to a qualified reviewer; capture success is not visual verification. |
| Worker has source access but no Unity bridge | Return source changes; another verified operator must exercise import/runtime and capture evidence. |
| Child cannot read coordinator's local output path | Transfer the actual artifact and verify access/revision before dependent analysis or import. |
| Image read is waiting on an external-directory permission | Record the access gate separately; resolve authorized access and test actual delivery before concluding anything about model vision. |
| Worker route/model changes mid-task | Recheck affected capabilities and input delivery; old capability evidence is insufficient. |
| QA report refers to an older UI screenshot | Capture/review the changed output revision before claiming final visual verification. |
