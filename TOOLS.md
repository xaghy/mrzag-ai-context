# TOOLS.md — Agent Arsenal
> Owner: Mohamed Abdalla
> Last Updated: 2026-03-18
> Purpose: Documents every agent and integration in Mohamed's AI stack. Update when tools are added, removed, or reconfigured.
> Linked to: AGENT.md Section 5 (Technical Profile)

---

## Agent Profiles

| Agent | Platform | Strengths | Use When |
|---|---|---|---|
| Claude | Claude Code CLI + Claude Desktop | Innovation, writing, complex reasoning, coding, file editing | Primary daily driver — most sessions |
| Gemini | Gemini CLI + Antigravity | Google ecosystem (Drive, Gmail, Calendar), system engineering | Google Workspace tasks, system health checks |
| Codex | Antigravity (OpenAI) | Code generation, refactoring, completions | Heavy coding sessions inside Antigravity |
| ChatGPT | Web / app | Legacy context (since 2023), broad general use | Historical context lookup, quick answers |

---

## Antigravity (Google Project IDX)

- **What it is:** Google's desktop AI IDE with multi-agent orchestration
- **Agents available inside:** Claude, Gemini, Codex — all orchestrated
- **Local file access:** Yes — desktop app, reads/writes local filesystem
- **VS Code extensions:** Yes — full VS Code extension ecosystem
- **Use when:** Multi-agent coding sessions, Mentats development work, anything requiring orchestrated agents in one IDE

---

## MCP Connections (Claude Code)

| MCP Server | Connected To | Status | Notes |
|---|---|---|---|
| GitHub | xaghy/mrzag-ai-context + other repos | Active | Context repo + code repos |
| Gmail | Mohamed's Gmail | Active | Read/draft emails |
| Google Calendar | Mohamed's Calendar | Active | Schedule + availability |
| Figma | Design files | Active | Design context |
| Gamma | Presentations | Active | Slide generation |
| Context7 | Library documentation | Active | Up-to-date docs lookup |
| Supabase | Database projects | Active | When building data-backed apps |
| Sentry | Error monitoring | Active | Production issue triage |
| Google Drive | WVI + Mentats Drive folders | Phase 2 | Antigravity handles natively for now |

---

## Handoff Patterns

| From | To | How |
|---|---|---|
| Claude → Gemini | Gemini CLI or Antigravity | Write SESSION_LOG.md entry. Note "Next Agent: Gemini." Gemini reads on "Sys Eng." |
| Gemini → Claude | Claude Code CLI | Same pattern. Gemini writes SESSION_LOG.md. Claude reads on "Sys Eng." |
| Any → Antigravity | Antigravity session | SESSION_LOG.md is local — Antigravity can read it directly. |
| This machine → Other device | Any agent | Push to GitHub repo. Clone on other device. SESSION_LOG.md travels with repo. |

---

## Integration Map

```
Mohamed
│
├─ Claude Code CLI ──── MCP: GitHub, Gmail, Calendar, Figma, Gamma, Context7, Supabase, Sentry
│       │
│       └─ Reads: AGENT.md (via ~/.claude/CLAUDE.md auto-load)
│                 SESSION_LOG.md (on "Sys Eng" trigger)
│                 TOOLS.md (on demand)
│
├─ Gemini CLI ──────── Native: Google Workspace, Event Viewer (System Sitrep)
│       │
│       └─ Reads: GEMINI.md (~/.gemini/GEMINI.md)
│                 SESSION_LOG.md (on "Sys Eng" trigger)
│
├─ Antigravity ─────── Orchestrates: Claude + Gemini + Codex
│       │
│       └─ Reads: Local files (desktop app)
│                 SESSION_LOG.md (on "Sys Eng" trigger)
│
└─ GitHub Repo ─────── xaghy/mrzag-ai-context
        │
        └─ Mirrors: AGENT.md, TOOLS.md, SESSION_LOG.md
                    (backup for cross-device access)
```
