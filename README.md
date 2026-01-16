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

### 2. Make executable (macOS/Linux only)

```bash
chmod +x netlist-mcp-darwin-arm64
```

### 3. Configure your MCP client

---

#### Claude Code

Use the CLI command:

```bash
claude mcp add netlist /path/to/netlist-mcp-darwin-arm64
```

Or edit `~/.claude.json`:

```json
{
  "mcpServers": {
    "netlist": {
      "command": "/path/to/netlist-mcp-darwin-arm64"
    }
  }
}
```

[Claude Code MCP Documentation](https://code.claude.com/docs/en/mcp)

---

#### Claude Desktop

Edit `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS) or `%APPDATA%\Claude\claude_desktop_config.json` (Windows):

```json
{
  "mcpServers": {
    "netlist": {
      "command": "/path/to/netlist-mcp-darwin-arm64"
    }
  }
}
```

---

#### VS Code (GitHub Copilot)

1. Open Command Palette (`Cmd+Shift+P` / `Ctrl+Shift+P`)
2. Search "MCP: Add Server"
3. Select "Add Local Server"
4. Enter server name: `netlist`
5. Enter command: `/path/to/netlist-mcp-darwin-arm64`

Or edit `.vscode/mcp.json` in your workspace:

```json
{
  "servers": {
    "netlist": {
      "command": "/path/to/netlist-mcp-darwin-arm64"
    }
  }
}
```

[VS Code MCP Documentation](https://code.visualstudio.com/docs/copilot/customization/mcp-servers)

---

#### Cursor

Edit `~/.cursor/mcp.json` (global) or `.cursor/mcp.json` (project):

```json
{
  "mcpServers": {
    "netlist": {
      "command": "/path/to/netlist-mcp-darwin-arm64"
    }
  }
}
```

Or use Command Palette: `Cmd+Shift+P` → "MCP: Add Server"

[Cursor MCP Documentation](https://cursor.com/docs/context/mcp)

---

#### Codex CLI (OpenAI)

Edit `~/.codex/config.toml`:

```toml
[mcp_servers.netlist]
command = "/path/to/netlist-mcp-darwin-arm64"
```

Or use the CLI:

```bash
codex mcp add netlist /path/to/netlist-mcp-darwin-arm64
```

[Codex CLI MCP Documentation](https://developers.openai.com/codex/mcp/)

---

#### Gemini CLI

Edit `~/.gemini/settings.json`:

```json
{
  "mcpServers": {
    "netlist": {
      "command": "/path/to/netlist-mcp-darwin-arm64"
    }
  }
}
```

Or use the CLI:

```bash
gemini mcp add --name netlist --command /path/to/netlist-mcp-darwin-arm64
```

[Gemini CLI MCP Documentation](https://geminicli.com/docs/tools/mcp-server/)

---

## Tools

| Tool | Description |
|------|-------------|
| `list_designs` | List design projects in a directory |
| `list_components` | List components by type (U, C, R, L, etc.) |
| `list_nets` | List all net names |
| `search_nets` | Regex search across net names |
| `search_components_by_refdes` | Regex search by refdes |
| `search_components_by_mpn` | Regex search by MPN |
| `search_components_by_description` | Regex search by description |
| `query_component` | Full component details and pin connections |
| `query_xnet_by_net_name` | Extended net connectivity from a net name |
| `query_xnet_by_pin_name` | Extended net connectivity from a pin |

## Usage Tips

- Use `list_designs` first to discover available projects
- `query_xnet_*` stops at power/ground nets; use `skip_types` (e.g., `['C', 'L']`) to skip series passives
- Cadence designs require exported `.dat` files (Tools → Create Netlist → PCB Editor format)

## Author

Valentino Zegna <valentino.zegna@gmail.com>

## License

MIT
