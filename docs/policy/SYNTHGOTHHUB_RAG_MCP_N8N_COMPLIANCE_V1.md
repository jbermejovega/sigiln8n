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
  - no_direct_default_branch_mutation

reject_if:
  - hidden_tool_call
  - unscoped_repository_write
  - connector_as_authority
  - credential_in_workflow_export
  - workflow_success_claimed_as_proof
  - missing_trace
  - source_provenance_erased
```

## QuasarPi plural-typed resource admission

The SIGILBOOK resource `QUASARPI_PLURAL_TYPED_QUNOS_MIMBREPI_LAURELPI_RENDER_LIVECODE_RESOURCE_V1` may be orchestrated only as a bounded review workflow.

```yaml
quasarpi_resource:
  source_authority: jbermejovega/sigilbook
  workflow_status: exported_inactive
  credentials: none
  external_calls: false
  repository_mutation: false
  stable_diffusion: plan_only
  sonic_pi: source_only
  kuirkode: declarative_boundary_validation
  human_review_required: true
```

The workflow must preserve QUNOS plurality, MimbrePi resource relations, LaurelPi boundary status, provenance, hashes, failures, and claim classes. It must reject implicit model downloads, automatic image generation, audio-server execution, webhook registration, and promotion without a replay witness.

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
QuasarPi routes a review plan only.
Stable Diffusion remains plan-only.
Sonic Pi remains source-only.
Failures remain visible.
Trace replays.
No identity transport.
PIORNALEGO ES CANON.
```
