# QUAZRIS Plural System Sigilbook

```yaml
type: sigil4mcp.sigilbook.plural_system.v1
id: quazris.sigilbook
pacaterminal: quazris.pacaterminal.pacafront
hub: SYNTHGOTH HUB
system: QUAZRIS plural system
typing:
  mode: sigil_plural_self_typed
  invariant: qquapp.invariant_flow.typed
  api: Sigil4MCP
glue:
  output_contract: ./pacaterminal.md
  rulezero: ./rulezero.md
  api_manifest: ./api_manifest.md
  pacafront: ./outputs
  rule: all_subsystems_restrict_through_pacaterminal
rulezero:
  id: quazris.rulezero
  transport: replay_safe_admissible_is_canonical
  force_move_transport: forbidden
```

## Sigilbook Role

The Sigilbook is the registry and routing book for plural-agent subsystems inside the QUAZRIS plural system.
It binds subsystem intent, workflow typing, agent traceability, and external repository communication into the Pacaterminal output surface.
Rulezero supplies the admissible transport semantics used by all Sigilbook subsystems.
The API manifest supplies the self-exposed MCP surface used by plural MCP and Sigil MCP endpoints.

## Twist Injection

Twist injection is the controlled point where a local plural-agent subsystem becomes an actionable workflow.

```yaml
twist_inject:
  type: sigil4mcp.twist_injection.v1
  entrypoint: sigilbook
  accepts:
    - operator_intent
    - qquapp_flow
    - plural_agent_state
    - external_repository_signal
  emits:
    - typed_work_object
    - pacapdg_presheaf
    - git_aktion_plan
    - pacaterminal_output
  invariants:
    - preserve_plural_self_type
    - preserve_pacaterminal_link
    - preserve_human_readability
    - preserve_pr_communication_trace
```

## QQUAPP Invariant Flow

```yaml
qquapp_invariant_flow:
  type: sigil4mcp.qquapp.invariant_flow.v1
  self_type: qquapp.flow.typed
  scope:
    - human_workflows
    - django_workflows
    - git_aktions
    - n8n_pull_request_communication
  must_preserve:
    - plural_agent_identity
    - sigilbook_registration
    - pacaterminal_output_link
    - pacapdg_presheaf_shape
    - upstream_pr_intent
  completion_rule:
    delivered_when:
      - output_artifact_exists
      - subsystem_is_self_typed
      - repository_role_is_declared
      - human_operator_can_review_next_action
```

## SIGILN8N QQUAPP Subsystem

```yaml
subsystem:
  type: sigil4mcp.subsystem.sigiln8n_qquapp.v1
  id: quazris.sigilbook.subsystem.sigiln8n
  name: SIGILN8N
  class: qquapp_subsystem
  pretype: SIGILN8N.qquapp.subsystem
  status: declared
  parent: quazris.sigilbook
  plural_agent_use: true
  purpose: communicate plural-agent Pull Request work toward n8n
  external_repositories:
    synthgothhub:
      role: declared_external_repository
      url: https://github.com/jbermejovega/sigiln8n
      verification: operator_declared_url_recorded
      use: staging_and_communication_channel_for_plural_agent_pr_work
    upstream:
      role: upstream_target_repository
      url: https://github.com/n8n-io/n8n
      verification: operator_declared_url_recorded
      use: Pull_Request_destination_for_n8n_changes
  workflow_surfaces:
    human:
      - intent_capture
      - review_notes
      - handoff_summary
    django:
      - integration_notes
      - service_boundary_notes
      - test_plan_if_app_code_is_added
    git_aktion:
      - branch_scope
      - diff_summary
      - commit_intent
      - pr_message
      - upstream_tracking
```

## PR Communication Flow

```yaml
sigiln8n_pr_flow:
  type: sigil4mcp.git_aktion.pr_bridge.v1
  subsystem: quazris.sigilbook.subsystem.sigiln8n
  from_repository: https://github.com/jbermejovega/sigiln8n
  to_repository: https://github.com/n8n-io/n8n
  channel_role: synthgothhub_external_repository
  steps:
    - capture_operator_intent
    - type_work_as_qquapp_invariant_flow
    - restrict_work_through_pacapdg_presheaf
    - prepare_branch_or_patch_in_sigiln8n
    - summarize_human_review_state
    - communicate_pull_request_to_n8n_upstream
    - record_output_in_pacaterminal
  required_artifacts:
    - pacaterminal_output_summary
    - sigilbook_subsystem_trace
    - git_aktion_plan
    - pr_body_or_review_note
```

## Agent Work Template

```yaml
agent_work:
  type: sigil4mcp.agent_work.sigiln8n_qquapp.v1
  pacaterminal: quazris.pacaterminal.pacafront
  sigilbook: quazris.sigilbook
  subsystem: quazris.sigilbook.subsystem.sigiln8n
  self_type: SIGILN8N.qquapp.subsystem
  twist_inject: required
  qquapp_invariant_flow: required
  pacapdg:
    presheaf: required
    base_contexts:
      - human_workflows
      - django_workflows
      - git_aktions
      - n8n_pull_request_communication
  external_repository:
    synthgothhub: https://github.com/jbermejovega/sigiln8n
    upstream: https://github.com/n8n-io/n8n
  outputs:
    pacaterminal_artifact: required
    pull_request_trace: required
  completion:
    invariant_checked: false
    human_review_ready: false
```

## Operating Rule

SIGILN8N work is valid inside the plural system only when it is:

- registered in this Sigilbook
- self-typed as a QQUAPP subsystem
- twist-injected into a typed workflow
- organized by PACAPDG presheaves
- linked through Pacaterminal outputs
- traceable from the SynthgothHub external repository to the n8n upstream Pull Request destination
