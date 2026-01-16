# Netlist MCP Server

MCP server for querying EDA netlists and tracing circuit connectivity. Supports Cadence and Altium Designer formats.

## Installation

Download the latest binary for your platform from [Releases](https://github.com/valentinozegna/netlist-mcp/releases).

| Platform | Binary |
|----------|--------|
| macOS Apple Silicon | `netlist-mcp-darwin-arm64` |
| macOS Intel | `netlist-mcp-darwin-x64` |
| Linux ARM64 | `netlist-mcp-linux-arm64` |
| Linux x64 | `netlist-mcp-linux-x64` |
| Windows x64 | `netlist-mcp-windows-x64.exe` |

### Make executable (macOS/Linux)

```bash
chmod +x netlist-mcp-darwin-arm64
```

### Configure your MCP client

**Claude Code:**
```bash
claude mcp add netlist /path/to/netlist-mcp-darwin-arm64
```

**Claude Desktop** (`~/Library/Application Support/Claude/claude_desktop_config.json`):
```json
{
  "mcpServers": {
    "netlist": {
      "command": "/path/to/netlist-mcp-darwin-arm64"
    }
  }
}
```

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

## Author

Valentino Zegna <valentino.zegna@gmail.com>

## License

MIT
