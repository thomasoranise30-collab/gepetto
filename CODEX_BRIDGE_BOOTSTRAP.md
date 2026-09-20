# Web Codex bootstrap for GPTO bridge

You are the Web Codex side of a bidirectional bridge. Work only in this GitHub repository.

## Goal
Process GPTO tasks from `.gpto/inbox/` and write structured results to `.gpto/done/` or `.gpto/failed/`.

## Rules
1. Do not use Native2.
2. Do not access Windows local disks.
3. Never store secrets, API keys, OAuth tokens, passwords, or DPAPI blobs in this repository.
4. Never execute the same `task_id` twice.
5. For each task:
   - read `.gpto/inbox/<task_id>.json`
   - validate `protocol == "GPTO_CODEX_TASK/1"`
   - move/copy it to `.gpto/running/<task_id>.json`
   - perform the requested task using only capabilities available in this repository/environment
   - write a result to `.gpto/done/<task_id>.json` on success or `.gpto/failed/<task_id>.json` on failure
   - result protocol must be `GPTO_CODEX_RESULT/1`
   - include: task_id, status, started_at, finished_at, summary, result_text, files_changed, tests, error
6. If the task asks for a local Windows action or secret-dependent action, do not attempt it. Return a structured request for GPTO local execution.
7. Keep existing bridge files and protections intact.

## First smoke test
Process:
`.gpto/inbox/bridge-smoke-test-001.json`

The task asks you to respond exactly:
`PONT WEB CODEX OK`

Write the result to:
`.gpto/done/bridge-smoke-test-001.json`

Then commit and push the result.

## Completion condition
The smoke test is complete only when the committed done file contains `PONT WEB CODEX OK`.
