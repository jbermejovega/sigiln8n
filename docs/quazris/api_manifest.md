# QUAZRIS API Manifest

```yaml
type: sigil4mcp.api_manifest.self_exposed_mcp.v1
id: quazris.api_manifest
pacaterminal: quazris.pacaterminal.pacafront
sigilbook: quazris.sigilbook
rulezero: quazris.rulezero
system: QUAZRIS plural system
mode: self_exposed_mcp
surfaces:
  - plural_mcp
  - sigil_mcp
  - pacaterminal_mcp
  - sigilbook_mcp
  - rulezero_mcp
typing:
  mode: plural_self_typed
  invariant: sigil_plural_self_typed
  transport: replay_safe_admissible
```

## Manifest Role

The API Manifest is the self-exposed MCP declaration for the QUAZRIS plural system.
It binds plural MCP, Sigil MCP, Pacaterminal, Sigilbook, and Rulezero into one typed interface surface.

## MCP Surfaces

```yaml
mcp_surfaces:
  plural_mcp:
    type: sigil4mcp.surface.plural_mcp.v1
    role: plural_agent_coordination
    exposes:
      - agent_work_objects
      - plural_self_types
      - pacapdg_presheaves
      - qquapp_flows
      - quasarpi_flows
  sigil_mcp:
    type: sigil4mcp.surface.sigil_mcp.v1
    role: typed_sigil_communication
    exposes:
      - sigil_events
      - boundary_decorators
      - coboundary_decorators
      - twist_injections
      - contextual_glue_diagnostics
  pacaterminal_mcp:
    type: sigil4mcp.surface.pacaterminal_mcp.v1
    role: output_and_delivery_front
    exposes:
      - output_contract
      - delivery_status
      - human_review_summary
      - agent_trace
  sigilbook_mcp:
    type: sigil4mcp.surface.sigilbook_mcp.v1
    role: subsystem_registry
    exposes:
      - subsystem_entries
      - external_repository_routes
      - qquapp_subsystems
      - sigiln8n_pr_bridge
  rulezero_mcp:
    type: sigil4mcp.surface.rulezero_mcp.v1
    role: admissible_transport_guard
    exposes:
      - no_force_move_transport
      - replay_safe_admissibility
      - boundary_coboundary_checks
      - context_induced_topologies
```

## Self-Exposed Contract

```yaml
self_exposed_contract:
  type: sigil4mcp.contract.self_exposed_mcp.v1
  every_endpoint_must:
    - declare_self_type
    - declare_mcp_surface
    - preserve_pacaterminal_link
    - preserve_sigilbook_registration
    - preserve_rulezero_transport
    - emit_human_reviewable_state
  forbidden:
    - untyped_endpoint
    - force_move_transport_endpoint
    - output_without_pacaterminal_link
    - subsystem_without_sigilbook_entry
```

## Endpoint Template

```yaml
endpoint:
  type: sigil4mcp.endpoint.v1
  id: null
  surface: plural_mcp | sigil_mcp | pacaterminal_mcp | sigilbook_mcp | rulezero_mcp
  self_type: required
  input:
    sigil: optional
    plural_state: optional
    workflow_context: optional
    boundary_data: optional
    coboundary_data: optional
  output:
    typed_result: required
    pacaterminal_artifact: optional
    agent_trace: required
  invariants:
    - sigil_plural_self_typed
    - replay_safe_admissible
    - context_recorded
```

## Operating Rule

An MCP interface is valid for the QUAZRIS plural system only when it is self-exposed through this manifest, plural self-typed, and compatible with Sigil MCP semantics.
No hidden, untyped, or force-transport endpoint is admissible.
