# Changelog — skill/websocket-reconnection

RL audit trail. Every version is a capsule finding the gate promoted into the
enterprise registry, distilled from a real Claude Code session via local Ollama.
Newest first. Versions follow semver (major/minor/patch).

## 1.0.0 — major — 2026-06-27T15:21:36.889Z  [published]
- **Learned from:** CAP-V006 (session `c5d81a37`, project `Beacon`, model `claude-opus-4-8`)
- **Finding:** On a dropped WebSocket, reconnect with jittered exponential backoff and a resumable session token — never tight-loop reconnect, which stampedes the server on mass disconnects.
- **Change:** New skill introduced for resilient WebSocket reconnection with jittered backoff and resumable sessions.
- **Tokens saved/use:** 828 · **Score delta:** +4 · **Adopted by:** 2 agent(s)
