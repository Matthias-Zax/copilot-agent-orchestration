---
name: postmortem-template
description: MUST be loaded automatically whenever an incident is classified as SEV-1 or SEV-2, or when generating an incident root-cause summary.
---
# Standardized Post-Mortem Template

Format the incident report strictly using the following Markdown structure:

## 🚨 Incident Post-Mortem Report
- **Severity**: [SEV-1 / SEV-2]
- **Affected Component**: [Service / File / Module]
- **Impact Summary**: Concise description of user or system impact.

### 🔍 Root Cause Analysis (5 Whys)
1. **Why did the failure occur?** ...
2. **Why was it not caught earlier?** ...
3. **Underlying architectural/code cause:** ...

### 🛠️ Immediate Remediation Plan
- [ ] Exact file and line to patch
- [ ] Verification test command to execute
