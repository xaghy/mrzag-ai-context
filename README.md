# mrzag-ai-context

Private context repository for Mohamed Abdalla's AI agent stack.

## What This Contains

| File | Purpose |
|---|---|
| `AGENT.md` | Person-level context — who Mohamed is, roles, priorities, behavioral rules |
| `TOOLS.md` | Tool arsenal — agents, MCP connections, handoff patterns |
| `SESSION_LOG.md` | Rolling session handoff log (max 3 entries) |

## New Device Setup

1. Clone this repo: `git clone https://github.com/xaghy/mrzag-ai-context`
2. Place `AGENT.md`, `TOOLS.md`, `SESSION_LOG.md` in `Documents\Claude\`
3. Create `~\.claude\CLAUDE.md`:
   - Symlink (preferred, run as admin): `cmd /c mklink "%USERPROFILE%\.claude\CLAUDE.md" "%USERPROFILE%\Documents\Claude\AGENT.md"`
   - Symlink requires Developer Mode (Settings → For Developers) OR elevated terminal
   - Fallback: copy AGENT.md content directly into `~\.claude\CLAUDE.md`
4. Register Event Log source (run PowerShell as admin, one-time):
   `New-EventLog -LogName Application -Source "AgentSession"`
5. Verify Claude Code auto-loads context on next session start

## GEMINI.md

Not in this repo. Managed separately. Place at `~\.gemini\GEMINI.md` on new devices.

## Sync Cadence

Push at end of session or before switching devices:
```bash
git add AGENT.md TOOLS.md SESSION_LOG.md
git commit -m "context sync YYYY-MM-DD"
git push
```
