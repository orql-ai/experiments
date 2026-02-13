# theORQL (SWE-bench Lite)

## Submission Info

- System: theORQL
- Split: SWE-bench Lite (`test`)
- Attempts: pass@1 (one prediction per instance)

## Results (sb-cli)

- Resolved (total): 213 / 300 (71.00%)
- Resolved (submitted): 213 / 300 (71.00%)
- Submitted: 300 / 300 (100%)
- Errors: 0
- sb-cli run_id: `theorql_lite_21986868008`
- sb-cli report JSON: `out/swebench/sbcli_reports/theorql_lite_21986868008/Subset.swe_bench_lite__test__theorql_lite_21986868008.json`

## System Summary

theORQL is a bounded patch-and-test agentic harness that:
- Reads the issue statement and relevant files, proposes minimal diffs, and runs repository tests.
- Maps issues to the right code by combining repository-wide search (symbols/strings), targeted file reads around likely entrypoints, and test-failure-driven refinement to quickly localize the minimal fix surface.
- Uses strict loop guardrails (max turns / max patch attempts / controlled tool access) to avoid churn.
- Prefers targeted tests first and iterates until either tests pass or caps are reached.

## Models Used

Primary model routed through OpenRouter:
- `moonshotai/kimi-k2.5`

## Resource Summary (This Run)

- Non-empty patches: 275 / 300
- Empty patches: 25 / 300
- Total tokens (in/out): 1,784,256,867 / 6,129,774
- Total tokens (sum): 1,790,386,641

## Compliance Notes

- No SWE-bench test-field usage: the agent does not receive or rely on SWE-bench evaluation fields (e.g. pass/fail phase test lists) as instructions.
- No hints usage: the `hints_text` field is not used by the agent.
- No web browsing: the harness executes in a sandboxed environment without external network access for test execution; any model browsing capability is not used for solution lookup.

## Artifacts Included

- `preds.json`: one prediction per instance
- `logs/<instance_id>/`: `patch.diff`, `test_output.txt`, `report.json`
- `trajs/<instance_id>.jsonl`: reasoning/trajectory traces per instance

## PR Checklist (copy into PR description)

- [x] Is a pass@1 submission (does not attempt the same task instance more than once)
- [x] Does not use SWE-bench evaluation-phase test lists or labels
- [x] Does not use the hints field in SWE-bench
- [x] Does not have web-browsing OR has taken steps to prevent lookup of SWE-bench solutions via web-browsing

## Compliance Note

This run is pass@1 with one prediction per instance. The harness does not expose SWE-bench evaluation-phase test lists or `hints_text` to the model; trace logs show `has_test_hints:false` throughout, and the default config disables hints/test-knowledge flags. Execution occurs in a sandboxed environment with no external web-browsing tool and test execution in Docker uses `--network none`, preventing lookup of SWE-bench solutions.

## Links (fill in)

- Report/blog: [Found Here](https://theorql.com/swe-bench)
- Code: Closed-source
- Authors: Shane Smitas https://www.linkedin.com/in/shanesmitas/
