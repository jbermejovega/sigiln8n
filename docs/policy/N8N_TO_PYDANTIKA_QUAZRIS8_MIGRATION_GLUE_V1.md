# n8n → PYDANTIKA → QUAZRIS8 Migration Glue V1

`sigiln8n` now acts as a migration surface only.

```text
legacy workflow JSON
  -> parse
  -> preserve dependency graph and failure paths
  -> externalize credential references
  -> type nodes as PYDANTIKA actions
  -> validate through QUAZRIS8 Q1..Q8
  -> emit migration trace
```

No direct canonical execution, repository authority, or certificate is granted by n8n workflow success.
