# MCP Pocket
[![smithery badge](https://smithery.ai/badge/@kazuph/mcp-pocket)](https://smithery.ai/server/@kazuph/mcp-pocket)

This is a connector to allow Claude Desktop (or any MCP client) to fetch your saved articles from Pocket API.

## Prerequisites
- Node.js (install via `brew install node`)
- Claude Desktop (install from https://claude.ai/desktop)
- Pocket API credentials

## Quick Start

1. Modify your Claude Desktop config located here:
`~/Library/Application\ Support/Claude/claude_desktop_config.json`

You can easily find this through the Claude Desktop menu:
1. Open Claude Desktop
2. Click Claude on the Mac menu bar
3. Click "Settings"
4. Click "Developer"

If you don't have this config, you can create an empty file at this location.

Add the following to the config file, replacing the credentials with your own:

```json
{
  "mcpServers": {
    "pocket": {
      "command": "npx",
      "args": ["-y", "@kazuph/mcp-pocket"],
      "env": {
        "POCKET_CONSUMER_KEY": "your-pocket-consumer-key",
        "POCKET_ACCESS_TOKEN": "your-pocket-access-token"
      }
    }
  }
}
```

## Development Setup

1. Clone this repository and install dependencies:
```bash
git clone https://github.com/kazuph/mcp-pocket.git
cd mcp-pocket
npm install
```

2. For development, use this configuration instead:
```json
{
  "mcpServers": {
    "pocket": {
      "command": "npx",
      "args": ["tsx", "/path/to/mcp-pocket/index.ts"],
      "env": {
        "POCKET_CONSUMER_KEY": "your-pocket-consumer-key",
        "POCKET_ACCESS_TOKEN": "your-pocket-access-token"
      }
    }
  }
}
```

### Development Commands

```bash
# Build TypeScript
npm run build

# Watch mode for development
npm run watch

# Publish to npm
npm login
npm publish
```

## Available Commands

The following MCP tools will be available in Claude Desktop:

- `pocket_get_articles`: Fetch your saved articles from Pocket API. Returns title, URL, and excerpt for each article.
- `pocket_mark_as_read`: Mark a specific article as read (archived) in your Pocket account using its item ID.

## Getting Pocket API Credentials

1. Visit [Pocket Developer Portal](https://getpocket.com/developer/)
2. Create a new app
3. Obtain your Consumer Key
4. Follow the [Pocket Authentication API](https://getpocket.com/developer/docs/authentication) process to get your Access Token

## License

MIT
