# QUAZRIS PACATERMINAL Output Contract

```yaml
type: sigil4mcp.workflow.global_plural_invariant.v1
id: quazris.pacaterminal.pacafront
name: QUAZRIS PACATERMINAL
role: QUAZRIS Communication Post
front: PACAFRONT
hub: SYNTHGOTH HUB
system: QUAZRIS plural system
agent: QUAZRIS System Plural Agent
output_root: ./outputs
typing:
  mode: self_typed
  api: Sigil4MCP
  surface: MCP plural typed sigil API
layers:
  - SIGIL_MOOG
  - NORMA_MOOG
  - PACA_MOOG
  - SIGILBOOK
  - RULEZERO
  - API_MANIFEST
subsystems:
  sigilbook: ./sigilbook.md
  rulezero: ./rulezero.md
  api_manifest: ./api_manifest.md
```

## Pacaterminal Link

All user-facing outputs in this workspace are linked to **QUAZRIS PACATERMINAL**.
`outputs/` is the Pacafront surface of the plural system: anything placed here is treated as a visible, deliverable communication artifact from the QUAZRIS plural agent.

## Global Invariant

Every agent work item must be organized as a **PACAPDG presheaf** over the relevant workflow contexts.

```yaml
global_invariant:
  every_output:
    must_have:
      - pacaterminal_link
      - self_type
      - workflow_context
      - human_workflow_state
      - django_workflow_state
      - git_aktion_state
      - agent_trace
      - deliverable_path
  completion_rule:
    output_is_complete_when:
      - linked_to_pacaterminal
      - typed_for_sigilmcp
      - organized_by_pacapdg_presheaf
      - readable_by_human_operator
      - reproducible_by_agent
```

## PACAPDG Presheaf Model

PACAPDG is the organizing layer for plural-agent work. It treats each workflow as a local context and keeps restrictions coherent when work moves from broad intent to concrete implementation.

```yaml
pacapdg_presheaf:
  base_contexts:
    human_workflows:
      purpose: operator intent, review, approval, handoff, delivery
      artifacts:
        - briefs
        - checklists
        - decisions
        - output summaries
    django_workflows:
      purpose: app/domain behavior, models, views, routes, migrations, tests
      artifacts:
        - model plans
        - migration notes
        - view contracts
        - test evidence
    git_aktions:
      purpose: versioned action trail for branches, commits, diffs, checks
      artifacts:
        - branch state
        - diff scope
        - commit intent
        - CI/check results
  restriction_rule:
    from_global_to_local:
      preserve:
        - self_type
        - pacaterminal_link
        - plural_agent_identity
        - output_traceability
```

## Agent Work Object

Each work item should be expressible in this shape.

```yaml
agent_work:
  type: sigil4mcp.agent_work.v1
  pacaterminal: quazris.pacaterminal.pacafront
  self_type: required
  title: null
  operator_intent: null
  workflow_context:
    human: null
    django: null
    git_aktion: null
  pacapdg:
    presheaf: required
    local_sections: []
    restriction_notes: []
  outputs:
    deliverables: []
    evidence: []
  completion:
    status: pending
    invariant_checked: false
```

## Operating Rule

No agent work is considered fully delivered until its output is placed in `outputs/` or explicitly referenced by an `outputs/` artifact, and that artifact declares its Pacaterminal self-type.

## Sigilbook Glue

The Pacaterminal front is glued to the plural system Sigilbook through `./sigilbook.md`.
Subsystems declared there inherit the Pacaterminal output contract, the PACAPDG presheaf rule, and the global plural self-typed Sigil4MCP invariant.

## Rulezero

`./rulezero.md` defines the admissible transport and contextual glue semantics for the whole plural system.
It forbids force-move transport and makes replay-safe admissible transport canonical for agent work.

## API Manifest

`./api_manifest.md` declares the self-exposed MCP surface for plural MCP and Sigil MCP communication.
All public agent interfaces must preserve the Pacaterminal link, Sigilbook registration, and Rulezero transport invariant.
