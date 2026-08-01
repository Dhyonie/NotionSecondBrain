# Notion Second Brain

A Claude Code project preconfigured with the [Notion MCP server](https://mcp.notion.com/mcp), so Claude can read and write your Notion workspace — your "second brain."

## Setup

1. Install Claude Code (if you haven't already):

   ```sh
   curl -fsSL https://claude.ai/install.sh | bash
   ```

2. Clone this repo and start Claude Code inside it:

   ```sh
   git clone https://github.com/Dhyonie/NotionSecondBrain.git
   cd NotionSecondBrain
   claude
   ```

3. On first launch, Claude Code will detect the project-scoped Notion MCP server in `.mcp.json` and ask you to approve it. The first time a Notion tool is used, your browser opens to authorize access to your Notion workspace via OAuth.

Use `/mcp` inside Claude Code to check connection status, reconnect, or re-authenticate.

## What's configured

`.mcp.json` registers Notion's hosted MCP server over HTTP transport:

```json
{
  "mcpServers": {
    "notion": {
      "type": "http",
      "url": "https://mcp.notion.com/mcp"
    }
  }
}
```

No API keys are stored in this repo — authentication happens through Notion's OAuth flow and credentials are kept locally on your machine.
