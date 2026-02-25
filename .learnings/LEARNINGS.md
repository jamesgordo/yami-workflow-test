## [LRN-20260225-001] correction

**Logged**: 2026-02-25T03:57:00Z
**Priority**: high
**Status**: pending
**Area**: infra | config

### Summary
Sub-agents require specific flags and notification commands for efficient, unattended completion.

### Details
The default configuration for `claude` (Claude Code) requires manual permissions for many operations, which causes background sub-agents to hang. Additionally, sub-agents do not automatically "wake" the orchestrator upon completion unless explicitly told to send a system event.

### Suggested Action
1.  Always use `--dangerously-skip-permissions` for `claude` in sub-agents.
2.  Include `openclaw system event --text "Done: [summary]" --mode now` in the sub-agent task prompt.
3.  Orchestrator should proactively poll sub-agents every ~5-10 minutes if no update is received.

### Metadata
- Source: user_feedback
- Related Files: SOUL.md, AGENTS.md
- Tags: workflow, automation, sub-agents
- See Also: ERR-20260225-001

---
