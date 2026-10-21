---
name: incident-triage
description: Entry point for triaging production incidents. Invoke manually via /incident-triage.
disable-model-invocation: true
---
# Incident Triage Workflow

1. **Delegate Execution**: Do NOT run this triage in the main agent context. Immediately invoke the `triage-specialist` custom agent as a subagent so its strict `model` (`claude-3-7-sonnet`) and read-only `tools` constraints are enforced.
2. **Subagent Task**: Have `triage-specialist` analyze the user's incident description, inspect logs/code, determine severity (SEV-1 to SEV-3), and automatically load the `postmortem-template` skill if rated SEV-1 or SEV-2.
3. **Output**: Return the subagent's structured triage report to the user.
