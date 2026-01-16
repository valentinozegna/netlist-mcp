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
# Move to a permanent location
mv netlist-mcp-darwin-arm64 ~/.local/bin/netlist-mcp
```

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
