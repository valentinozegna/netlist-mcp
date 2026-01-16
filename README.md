# Netlist MCP Server

MCP server for querying EDA netlists and tracing circuit connectivity. Supports Cadence (CIS, HDL) and Altium Designer formats.

**macOS binaries are signed and notarized by Apple.**

## Quick Install

```bash
curl -fsSL https://raw.githubusercontent.com/valentinozegna/netlist-mcp/main/install.sh | bash
```

This will:
- Download the correct binary for your platform
- Verify the checksum
- Install to `~/.netlist-mcp/bin/`
- Add to your PATH

## Update

```bash
netlist-mcp --update
```

Or the binary will auto-update on startup (disable with `NETLIST_MCP_NO_UPDATE=1`).

## Configure your MCP client

After installation, configure your MCP client to use the server.

### Claude Code

```bash
claude mcp add netlist ~/.netlist-mcp/bin/netlist-mcp
```

### Claude Desktop

Add to `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS):

```json
{
  "mcpServers": {
    "netlist": {
      "command": "~/.netlist-mcp/bin/netlist-mcp"
    }
  }
}
```

### VS Code (Copilot/Continue)

Add to `.vscode/mcp.json` in your project:

```json
{
  "servers": {
    "netlist": {
      "command": "~/.netlist-mcp/bin/netlist-mcp"
    }
  }
}
```

### Cursor

Add to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "netlist": {
      "command": "~/.netlist-mcp/bin/netlist-mcp"
    }
  }
}
```

## Supported Platforms

| Platform | Binary | Status |
|----------|--------|--------|
| macOS Apple Silicon | `netlist-mcp-darwin-arm64` | Signed & Notarized |
| macOS Intel | `netlist-mcp-darwin-x64` | Signed & Notarized |
| Linux ARM64 | `netlist-mcp-linux-arm64` | |
| Linux x64 | `netlist-mcp-linux-x64` | |
| Windows x64 | `netlist-mcp-windows-x64.exe` | |

## MCP Tools

All tools accept absolute design paths. DNS (Do Not Stuff) components are excluded by default unless `include_dns=true` is provided.

| Tool | Description |
|------|-------------|
| `list_designs` | List design projects in a directory |
| `list_components` | List components by type prefix (U, C, R, L, etc.) |
| `list_nets` | List all net names |
| `search_nets` | Regex search across net names |
| `search_components_by_refdes` | Regex search by refdes |
| `search_components_by_mpn` | Regex search by MPN |
| `search_components_by_description` | Regex search by description |
| `query_component` | Full component details and pin connections |
| `query_xnet_by_net_name` | Extended net connectivity from a net name |
| `query_xnet_by_pin_name` | Extended net connectivity from a pin (REFDES.PIN) |

## Usage Tips

- Use `list_designs` first to discover available projects in a directory
- `query_xnet_*` stops traversal at power/ground nets; use `skip_types` (e.g., `['C', 'L']`) to skip series passives
- Cadence designs require exported `.dat` files (Tools > Create Netlist > PCB Editor format)

## License

MIT
