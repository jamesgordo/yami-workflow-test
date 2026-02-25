## [ERR-20260225-001] subagent_stall_and_auth_error

**Logged**: 2026-02-25T03:55:00Z
**Priority**: high
**Status**: pending
**Area**: infra | config

### Summary
Architect and Developer sub-agents stalled during implementation; Architect hit a 401 error.

### Error
```
Cloud Code Assist API error (401): Request had invalid authentication credentials.
```

### Context
- Architect sub-agent ran for 25m, eventually hit 401.
- Developer sub-agent ran for 45m, stalled on manual permission prompts.

### Suggested Fix
- Use `--dangerously-skip-permissions` for Claude Code in sub-agents.
- Ensure sub-agents have the `openclaw system event` notification command in their task description.
- Investigate 401 error (likely token expiration during long runs).

### Metadata
- Reproducible: unknown
- Related Files: docs/plans/implement-tailwind/
- See Also: LRN-20260225-001

---
