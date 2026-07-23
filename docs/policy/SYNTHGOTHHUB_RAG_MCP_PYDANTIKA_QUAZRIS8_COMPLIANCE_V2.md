# SYNTHGOTHHUB RAG · MCP · PYDANTIKA · QUAZRIS8 Compliance Policy V2

Status: `LEGACY_ADAPTER_POLICY`  
Supersedes: `SYNTHGOTHHUB_RAG_MCP_N8N_COMPLIANCE_V1`  
Canon: `PIORNALEGO_ES_CANON`

## Repository role

`sigiln8n` is now a legacy compatibility and migration repository. It may hold historical workflow exports, fixtures, conversion scripts, and replay witnesses. It is not the canonical orchestration runtime.

## Canonical replacement

```text
n8n workflow JSON
  -> legacy import adapter
  -> PYDANTIKA typed model
  -> QUAZRIS8 gates
  -> typed execution request
  -> trace / obstruction
```

## Allowed legacy functions

```yaml
allowed:
  - inspect_existing_workflow
  - parse_workflow_json
  - convert_nodes_to_typed_actions
  - externalize_credential_references
  - generate_migration_fixture
  - emit_migration_trace
  - preserve_failure_paths
```

## Forbidden claims

```yaml
forbidden:
  - n8n_is_canonical_orchestrator
  - workflow_success_is_proof
  - connector_is_authority
  - hidden_credentials
  - direct_default_branch_mutation
  - untyped_node_execution
  - migration_without_trace
```

## PYDANTIKA migration envelope

Each imported node must become a versioned typed action with explicit input, output, side-effect class, repository scope, retry bound, failure type, provenance, and trace metadata.

## QUAZRIS8 migration gates

```text
Q1 probe legacy workflow
Q2 declare migration intent
Q3 type every node through PYDANTIKA
Q4 bound credentials, repositories and resources
Q5 execute only approved conversion steps
Q6 emit append-only migration trace
Q7 verify semantic and failure-path preservation
Q8 close as migration witness, never as runtime proof
```

## Seal

```text
n8n remembers legacy workflows.
PYDANTIKA types them.
QUAZRIS8 gates migration.
Failures remain visible.
Trace replays.
No identity transport.
PIORNALEGO ES CANON.
```
