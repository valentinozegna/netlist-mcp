# Netlist MCP Server

MCP server for querying EDA netlists and tracing circuit connectivity. Supports Cadence (CIS, HDL) and Altium Designer formats.

## Installation

### 1. Download

Download the latest binary for your platform from [Releases](https://github.com/valentinozegna/netlist-mcp/releases).

| Platform | Binary |
|----------|--------|
| macOS Apple Silicon | `netlist-mcp-darwin-arm64` |
| macOS Intel | `netlist-mcp-darwin-x64` |
| Linux ARM64 | `netlist-mcp-linux-arm64` |
| Linux x64 | `netlist-mcp-linux-x64` |
| Windows x64 | `netlist-mcp-windows-x64.exe` |

### 2. Prepare the binary

**macOS:**
```bash
# Remove quarantine attribute (required for unsigned binaries)
xattr -d com.apple.quarantine netlist-mcp-darwin-arm64

# Make executable
chmod +x netlist-mcp-darwin-arm64

# Move to a permanent location
mv netlist-mcp-darwin-arm64 ~/.local/bin/netlist-mcp
```

**Linux:**
```bash
# Make executable
chmod +x netlist-mcp-linux-x64

# Move to a permanent location
mv netlist-mcp-linux-x64 ~/.local/bin/netlist-mcp
```

**Windows:**
1. Right-click `netlist-mcp-windows-x64.exe` → **Properties**
2. Check **Unblock** at the bottom → Click **Apply**
3. Move to a permanent location (e.g., `C:\Users\<you>\bin\netlist-mcp.exe`)

*Or if SmartScreen blocks it: Click "More info" → "Run anyway"*

### 3. Configure your MCP client

---

## Project-Local Configuration

Add to your project's MCP config file to enable **only for that repository**.

#### Claude Code

Create `.mcp.json` in your project root:

```json
{
  "mcpServers": {
    "netlist": {
      "command": "/path/to/netlist-mcp"
    }
  }
}
```

[Claude Code MCP Docs](https://code.claude.com/docs/en/mcp)

---

#### VS Code (GitHub Copilot)

Create `.vscode/mcp.json` in your project:

```json
{
  "servers": {
    "netlist": {
      "command": "/path/to/netlist-mcp"
    }
  }
}
```

[VS Code MCP Docs](https://code.visualstudio.com/docs/copilot/customization/mcp-servers)

---

#### Cursor

Create `.cursor/mcp.json` in your project root:

```json
{
  "mcpServers": {
    "netlist": {
      "command": "/path/to/netlist-mcp"
    }
  }
}
```

[Cursor MCP Docs](https://cursor.com/docs/context/mcp)

---

#### Codex CLI (OpenAI)

Create `.codex/config.toml` in your project root:

```toml
[mcp_servers.netlist]
command = "/path/to/netlist-mcp"
```

[Codex CLI MCP Docs](https://developers.openai.com/codex/mcp/)

---

#### Gemini CLI

Create `.gemini/settings.json` in your project root:

```json
{
  "mcpServers": {
    "netlist": {
      "command": "/path/to/netlist-mcp"
    }
  }
}
```

[Gemini CLI MCP Docs](https://geminicli.com/docs/tools/mcp-server/)

---

## Global Installation (CLI)

Install globally to enable **across all projects**.

| App | Command |
|-----|---------|
| Claude Code | `claude mcp add netlist /path/to/netlist-mcp --scope user` |
| Codex CLI | `codex mcp add netlist /path/to/netlist-mcp` |
| Gemini CLI | `gemini mcp add --name netlist --command /path/to/netlist-mcp --scope user` |

For VS Code and Cursor, use their Command Palette (`Cmd+Shift+P`) → "MCP: Add Server" to add globally.

---

## Author

Valentino Zegna <valentino.zegna@gmail.com>

## License

MIT
