# Netlist MCP Server

MCP server for querying EDA netlists and tracing circuit connectivity. Supports Cadence (CIS, HDL) and Altium Designer formats.

## Quick Install

```bash
curl -fsSL https://raw.githubusercontent.com/valentinozegna/netlist-mcp/main/install.sh | bash
```

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
