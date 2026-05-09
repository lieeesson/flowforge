# FlowForge

Enforced workflow engine for AI agents — YAML-defined, CLI-driven state machine that prevents agents from skipping steps.

## Install

```bash
pip install flowforge
```

## Quick Start

### 1. Create a workflow YAML

```yaml
name: my-workflow
description: Example workflow
start: plan

nodes:
  plan:
    task: Plan the implementation
    next: execute

  execute:
    task: Execute the plan
    next: review

  review:
    task: Review the results
    terminal: true
```

Save this as `workflows/my-workflow.yaml` (FlowForge auto-discovers workflows from the `workflows/` directory).

### 2. Run the workflow

```bash
# Workflows are auto-loaded from workflows/ directory
flowforge list

# Start an instance
flowforge start my-workflow

# Check current status
flowforge status

# Complete current node and advance
flowforge next

# View execution history
flowforge log
```

## CLI Commands

| Command | Description |
|---------|-------------|
| `flowforge define <yaml>` | Register or update a workflow |
| `flowforge start <workflow>` | Start new workflow instance |
| `flowforge status` | Show current node, task, and branches |
| `flowforge next [--branch N]` | Complete current node and advance |
| `flowforge log` | View execution history |
| `flowforge list` | List all defined workflows |
| `flowforge active` | List active workflow instances |
| `flowforge reset` | Reset current instance to start |
| `flowforge run <workflow>` | Start (or resume) workflow and output next action as JSON |
| `flowforge advance` | Advance workflow with result and output next action as JSON |

## License

MIT