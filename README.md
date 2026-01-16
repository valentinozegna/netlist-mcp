# Netlist MCP Server

MCP server for querying EDA netlists and tracing circuit connectivity. Supports Cadence (CIS, HDL) and Altium Designer formats.

## Quick Install

```bash
curl -fsSL https://raw.githubusercontent.com/valentinozegna/netlist-mcp/main/install.sh | bash
```

## Update

The binary will auto-update on startup. To update manually:

```bash
netlist-mcp --update
```

## Configure your MCP client

After installation, configure your MCP client. Replace `/Users/YOUR_USERNAME` with your actual home directory path.

### Claude Code

```bash
claude mcp add netlist /Users/YOUR_USERNAME/.netlist-mcp/bin/netlist-mcp
```

### Claude Desktop

Add to `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS):

```json
{
  "mcpServers": {
    "netlist": {
      "command": "/Users/YOUR_USERNAME/.netlist-mcp/bin/netlist-mcp"
    }
  }
}
```

### VS Code (GitHub Copilot)

Add to `.vscode/mcp.json` in your project:

```json
{
  "servers": {
    "netlist": {
      "type": "stdio",
      "command": "/Users/YOUR_USERNAME/.netlist-mcp/bin/netlist-mcp"
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
      "command": "/Users/YOUR_USERNAME/.netlist-mcp/bin/netlist-mcp"
    }
  }
}
```

## Supported Platforms

| Platform | Binary |
|----------|--------|
| macOS Apple Silicon | `netlist-mcp-darwin-arm64` |
| macOS Intel | `netlist-mcp-darwin-x64` |
| Linux ARM64 | `netlist-mcp-linux-arm64` |
| Linux x64 | `netlist-mcp-linux-x64` |
| Windows x64 | `netlist-mcp-windows-x64.exe` |
