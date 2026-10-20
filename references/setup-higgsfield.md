# Connecting Higgsfield

Every user connects their own Higgsfield account. Generation uses their
credits. Sign-in happens in the browser (OAuth); there is no API key to
copy, and nobody should ever paste a key or token into the chat.

Server URL: `https://mcp.higgsfield.ai/mcp`

1. Make a Higgsfield account at higgsfield.ai and get some credits (a
   paid plan or a credit pack). Video needs a paid plan for some models.
2. Connect it in the app you're using:

**Claude Code** (terminal or the desktop app's Code tab)
- Run: `claude mcp add --transport http higgsfield https://mcp.higgsfield.ai/mcp`
- Then in a `claude` session run `/mcp`, pick `higgsfield`, and sign in
  in the browser.

**claude.ai or Claude Desktop (chat)**
- Settings, Connectors, Add custom connector. Name `Higgsfield`, URL
  `https://mcp.higgsfield.ai/mcp`. Click Connect and sign in.
- Turn the connector on in the chat (the tools menu) before starting.

**ChatGPT**
- Higgsfield has an official ChatGPT plugin. Install it from
  `chatgpt.com/plugins/higgsfield` and sign in, then mention
  `@Higgsfield` in the chat.
- If that isn't available on your plan, ChatGPT's developer mode can
  add a custom connector with the URL above.

**Codex (OpenAI's coding agent)**
- Add to `~/.codex/config.toml`:
  ```toml
  [mcp_servers.higgsfield]
  url = "https://mcp.higgsfield.ai/mcp"
  ```
- Then run `codex mcp login higgsfield` and sign in.

**Anything else** that supports remote MCP servers: add the URL above
as a streamable HTTP server and sign in when prompted.

3. Check it works: ask "what's my Higgsfield credit balance?". The
   assistant should answer from the Higgsfield tool, not from memory.

## Troubleshooting
- **"Unauthorized" mid-project:** the sign-in expired. Reconnect
  (`/mcp` in Claude Code, or reconnect the connector) and continue.
- **Cloud or sandboxed sessions** may block outbound connections to
  `mcp.higgsfield.ai`. Run locally or allow that domain.
- **Rate limits (429):** the request was refused and not charged. Wait
  a little and resubmit unchanged.
- **Tool names change.** List the server's tools at the start of each
  session rather than assuming names.

These steps were current in October 2026. Apps rename menus often; if a
step doesn't match what the user sees, use the closest current label.
