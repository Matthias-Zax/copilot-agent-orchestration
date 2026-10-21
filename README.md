# Copilot Agent Orchestration

This repository demonstrates how to chain **Entry-Point Skills**, **Custom Agents** (with locked `model:` and `tools:`), **Auto-Invoked Skills**, and **Agent Handoffs** in VS Code.

## Repository Structure

```text
.github/
├── agents/
│   ├── triage-specialist.agent.md       # Read-only SRE agent (Claude 3.7 Sonnet) + Handoff button
│   └── hotfix-engineer.agent.md         # Write-enabled patching agent (GPT-4o)
├── skills/
│   ├── incident-triage/
│   │   └── SKILL.md                     # Manual entry-point (/incident-triage) -> delegates to subagent
│   └── postmortem-template/
│       └── SKILL.md                     # Auto-invoked skill (loaded automatically on SEV-1/SEV-2)
└── prompts/
    └── incident-triage.prompt.md        # Optional legacy prompt (if using the 'Local' session target)
```

## Workflow

1. **Trigger Entry Point**: Run `/incident-triage` in chat.
2. **Subagent Execution**: The entry-point skill delegates work to `@triage-specialist` (enforcing `claude-3-7-sonnet` and read-only tools).
3. **Auto-Invoked Skill**: For SEV-1 or SEV-2 incidents, the agent loads and formats output via `postmortem-template`.
4. **Handoff**: The triage report includes a handoff action to transfer the root-cause diagnosis to `@hotfix-engineer` (using `gpt-4o` with write access).
