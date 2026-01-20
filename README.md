# Netlist MCP Server

MCP server for querying EDA netlists and tracing circuit connectivity. Supports Cadence (CIS, HDL) and Altium Designer formats.

## Quick Install

**macOS / Linux:**

```bash
curl -fsSL https://raw.githubusercontent.com/valentinozegna/netlist-mcp/main/install.sh | bash
```

**Windows (PowerShell):**

```powershell
irm https://raw.githubusercontent.com/valentinozegna/netlist-mcp/main/install.ps1 | iex
```

## Update

The binary will auto-update on startup. To update manually:

```bash
netlist-mcp --update
```

## Configure your MCP client

After installation, configure your MCP client. The binary installs to:
- **macOS/Linux:** `~/.netlist-mcp/bin/netlist-mcp`
- **Windows:** `%LOCALAPPDATA%\netlist-mcp\bin\netlist-mcp.exe`

### Claude Code

```bash
claude mcp add netlist netlist-mcp
```

### Claude Desktop

Add to your Claude Desktop config:
- **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "netlist": {
      "command": "netlist-mcp"
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
      "command": "netlist-mcp"
    }
  }
}
```

### Cursor

Add to `.cursor/mcp.json` in your project:

```json
{
  "mcpServers": {
    "netlist": {
      "command": "netlist-mcp"
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
| Windows ARM64 | `netlist-mcp-windows-x64-baseline.exe` (emulated) |
