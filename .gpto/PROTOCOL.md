# Protocol

## Task

```json
{
  "protocol": "GPTO_CODEX_TASK/1",
  "task_id": "unique-id",
  "created_at": "ISO-8601",
  "prompt": "...",
  "priority": "normal",
  "allow_write": true,
  "allow_external_action": false,
  "context_refs": []
}
```

## Result

```json
{
  "protocol": "GPTO_CODEX_RESULT/1",
  "task_id": "unique-id",
  "status": "SUCCESS",
  "started_at": "ISO-8601",
  "finished_at": "ISO-8601",
  "summary": "...",
  "result_text": "...",
  "files_changed": [],
  "tests": {},
  "error": null
}
```
