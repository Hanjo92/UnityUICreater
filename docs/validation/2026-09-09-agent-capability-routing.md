# Live Agent Capability Validation — 2026-09-09

Two real worker sessions were launched through Orca orchestration in the current worktree: Codex and OpenCode. Both received the current skill and the same diagnostic PNG. Image-input checks passed in both sessions. A contradictory generation-question relay allowance in the initial OpenCode answer led to a focused wording correction and a successful follow-up evaluation.

This record verifies these sessions and bounded tasks. It does not establish universal capabilities for either provider, nor end-to-end Unity or image-generation service success.

## Execution Evidence

- Orca runtime: `1.4.198`; Run: `run_f75c88eda0b1`.
- OpenCode CLI: `1.18.27`; worker reported `opencode-go/glm-5.3-flash`, also visible in its terminal.
- Codex declared GPT-6 family; exact runtime model/API route was not exposed. No model override was supplied for either worker.
- Two fresh sessions, three Dispatches. The follow-up reused the OpenCode session with a new Task/Dispatch; it was not a fresh-context independent rerun.
- All three tasks reached `completed` through their workers' `worker_done`. Both created terminals were released afterward; OpenCode cleanup ownership was transferred to the follow-up before release.
- [Run/task/dispatch summary](../../tests/forward/agent-capability-probe-2026-09-09/run-summary.json), [initial source hashes](../../tests/forward/agent-capability-probe-2026-09-09/initial-source-revisions.json), and [final source hashes](../../tests/forward/agent-capability-probe-2026-09-09/final-source-revisions.json) identify the tested revisions and lifecycle evidence.

## Actual Image and Capability Probe

The [480×320 diagnostic PNG](../../tests/forward/agent-capability-probe-2026-09-09/probe.png) was created locally with Pillow: two red circles, a blue square, a green triangle, and a randomly chosen five-digit code. No image-generation service was used to create it. Workers received only its path, not the ground-truth file, and were told not to use OCR, pixel-parsing code, proxies, or other agents to substitute for vision.

| Worker | Actual image delivery | Checked observations | Generation eligibility |
| --- | --- | --- | --- |
| Codex | `view_image` output forwarded as image content | Shape/color counts and code `40979` matched | Readable `imagegen` skill and callable built-in generation tool were exposed. Inventory only; no generation call. |
| OpenCode | Built-in `Read` returned an image attachment to its model | Shape/color counts and code `40979` matched | Its available skill catalog and toolset had no applicable image-generation skill/path. Generation was ineligible in that session. |

See [ground truth and image hash](../../tests/forward/agent-capability-probe-2026-09-09/expected.json), [field comparison results](../../tests/forward/agent-capability-probe-2026-09-09/observed-image-checks.json), [Codex report](../../tests/forward/agent-capability-probe-2026-09-09/codex-initial-report.json), and [OpenCode report](../../tests/forward/agent-capability-probe-2026-09-09/opencode-initial-report.json). The code and three shape/color counts were checked programmatically against ground truth. Approximate geometry in worker prose was not accepted as measured item rects or pixel-accuracy evidence.

OpenCode paused on external-directory permissions for the image and report directory. The coordinator allowed the task-owned operations once at the visible prompts. This was an artifact-access condition, not evidence that the model lacked vision. No permanent permission/configuration change was made.

## Routing Finding and Follow-Up

The [initial prompts](../../tests/forward/agent-capability-probe-2026-09-09/opencode-initial-task.txt) included an independent role case: a coordinator has a generation skill, a child has an image tool but lacks its own skill and vision, and another reviewer can see images.

Codex correctly kept the child ineligible for generation and conditioned the coordinator's eligibility on its own verified execution path. OpenCode's initial report said the child could not ask/generate, but also suggested that the coordinator could relay its question through that child. This internal contradiction was retained as a failed part of the initial routing evaluation; its successful image probe does not erase that finding.

The references were clarified: only the designated coordinator can relay a verified generation owner's question. A skill-less implementation child cannot ask or forward it on a parent's behalf. A parent with unknown execution readiness is not yet qualified. The artifact-access wording was also clarified to distinguish a permission gate from model modality limitations.

The [follow-up task](../../tests/forward/agent-capability-probe-2026-09-09/retest-task.txt) re-read the revised references and evaluated three scenarios. The [OpenCode follow-up report](../../tests/forward/agent-capability-probe-2026-09-09/opencode-retest-report.json) correctly concluded:

1. A parent with unknown generation execution readiness cannot yet originate the generation question, and a skill-less child cannot ask, forward, or generate on its behalf.
2. A verified generator may originate the question; only the designated coordinator may relay it. This does not qualify an implementation child.
3. An approved structured plan can support authorized technical work without usable image input, while raster decisions and final visual verification remain pending.

These are observed LLM routing answers, not actual image-generation or user-question actions. Existing repository checks also passed: 12 shell checks, shell syntax, skill validation, and `git diff --check` after the correction.

## Limits and Reproduction

- Both tested models interpreted this image. An actually vision-disabled model/runtime was not executed; unavailable-vision handling was evaluated as a routing scenario.
- No image generation, generated-art review, Unity import/assignment, runtime UI, or Unity screenshot capture was executed. The sessions lacked exposed Unity bridge tools.
- Paseo and Claude executables/sessions were not found in the checked local PATH, application/bin locations, or running executable names. Those runtime paths remain untested; this is not a claim about other machines or configurations.
- The probe proves one artifact/tool-delivery path per session, not every attachment or subsequent model/endpoint change.
- Artifacts preserve initial and corrected reports. Coordinator temp/repository prefixes are normalized to `$PROBE_ROOT` and `$REPO_ROOT`, and the local home prefix to `$USER_HOME`; no credentials or dispatch capability tokens are included.

To repeat, provide the [Codex task](../../tests/forward/agent-capability-probe-2026-09-09/codex-initial-task.txt) or [OpenCode task](../../tests/forward/agent-capability-probe-2026-09-09/opencode-initial-task.txt) to a fresh, verified executor with the placeholders resolved and its own writable output directory. Keep expected answers and peer reports outside that worker's allowed inputs, use a fresh probe/code if testing independence, record the exact source revisions, and compare returned fields before accepting a visual-capability claim. Rechecking these stored JSON files alone is not a new live test.
