# SYNTHGOTHHUB RAG · MCP · n8n Compliance Policy V1

Status: `ACTIVE_ORCHESTRATION_POLICY`  
Canon: `PIORNALEGO_ES_CANON`

## Role

`sigiln8n` is the orchestration runtime for typed SYNTHGOTHHUB workflows. It does not become the knowledge authority, identity kernel, or source-of-truth repository.

## Required workflow chain

```text
validated trigger
  -> typed RAG retrieval
  -> provenance check
  -> MCP boundary check
  -> n8n node execution
  -> trace event
  -> obstruction or witness
  -> PACAPDG projection request
```

## Compliance gates

```yaml
required:
  - input_schema_versioned
  - repository_boundary_declared
  - credentials_externalized
  - secret_values_not_committed
  - tool_calls_visible
  - human_review_for_mutations
  - retries_bounded
  - failures_preserved
  - trace_append_only
  - replay_metadata_present
  - no_direct_main_mutation

reject_if:
  - hidden_tool_call
  - unscoped_repository_write
  - connector_as_authority
  - credential_in_workflow_export
  - workflow_success_claimed_as_proof
  - missing_trace
  - source_provenance_erased
```

## Workflow status vocabulary

- `planned`: design only;
- `exported`: workflow JSON exists;
- `tested`: fixture or dry-run witness exists;
- `replayable`: execution trace and input versions exist;
- `production`: credentials, rollback, monitoring, and review gates exist.

No higher status may be claimed without its witnesses.

## Repository mutation policy

```text
read
-> branch
-> diff
-> validate
-> draft PR
-> review
-> merge only after explicit authorization
```

## Seal

```text
RAG retrieves.
MCP bounds tools.
n8n orchestrates.
Failures remain visible.
Trace replays.
No identity transport.
```
