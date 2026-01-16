# ⚡ Netlist MCP Server

**Give your AI agent the power to understand circuit schematics.**

Connect Claude, Copilot, Cursor, Codex, or Gemini to your EDA netlists. Query components, trace signal paths, and analyze circuit connectivity — all through natural conversation.

Supports **Cadence** (CIS, HDL) and **Altium Designer** formats.

---

## 🚀 Installation

### 1. Download

Grab the latest binary for your platform from [**Releases**](https://github.com/valentinozegna/netlist-mcp/releases).

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
xattr -d com.apple.quarantine netlist-mcp-darwin-arm64
chmod +x netlist-mcp-darwin-arm64
mv netlist-mcp-darwin-arm64 ~/.local/bin/netlist-mcp
```

**Linux:**
```bash
chmod +x netlist-mcp-linux-x64
mv netlist-mcp-linux-x64 ~/.local/bin/netlist-mcp
```

**Windows:**
1. Right-click the `.exe` → **Properties** → Check **Unblock** → **Apply**
2. Move to a permanent location (e.g., `C:\Users\<you>\bin\netlist-mcp.exe`)

---

## 🔧 Configuration

### Project-Local Setup

Enable the MCP server **only for a specific project** by adding a config file to your repository.

<details>
<summary><b>Claude Code</b> — <code>.mcp.json</code></summary>

```json
{
  "mcpServers": {
    "netlist": {
      "command": "/path/to/netlist-mcp"
    }
  }
}
```
[Documentation →](https://code.claude.com/docs/en/mcp)
</details>

<details>
<summary><b>VS Code (Copilot)</b> — <code>.vscode/mcp.json</code></summary>

```json
{
  "servers": {
    "netlist": {
      "command": "/path/to/netlist-mcp"
    }
  }
}
```
[Documentation →](https://code.visualstudio.com/docs/copilot/customization/mcp-servers)
</details>

<details>
<summary><b>Cursor</b> — <code>.cursor/mcp.json</code></summary>

```json
{
  "mcpServers": {
    "netlist": {
      "command": "/path/to/netlist-mcp"
    }
  }
}
```
[Documentation →](https://cursor.com/docs/context/mcp)
</details>

<details>
<summary><b>Codex CLI</b> — <code>.codex/config.toml</code></summary>

```toml
[mcp_servers.netlist]
command = "/path/to/netlist-mcp"
```
[Documentation →](https://developers.openai.com/codex/mcp/)
</details>

<details>
<summary><b>Gemini CLI</b> — <code>.gemini/settings.json</code></summary>

```json
{
  "mcpServers": {
    "netlist": {
      "command": "/path/to/netlist-mcp"
    }
  }
}
```
[Documentation →](https://geminicli.com/docs/tools/mcp-server/)
</details>

---

### Global Installation

Enable across **all projects** using CLI commands:

| App | Command |
|-----|---------|
| Claude Code | `claude mcp add netlist /path/to/netlist-mcp --scope user` |
| Codex CLI | `codex mcp add netlist /path/to/netlist-mcp` |
| Gemini CLI | `gemini mcp add --name netlist --command /path/to/netlist-mcp --scope user` |

For **VS Code** and **Cursor**, use Command Palette (`Cmd+Shift+P`) → "MCP: Add Server"

---

## 📄 License

MIT

---

Built by [Valentino Zegna](mailto:valentino.zegna@gmail.com)
