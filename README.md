# zihin.io- Agent Marketplace for izan.io

Community-driven marketplace where anyone can discover, share, and contribute AI agents for [izan.io](https://izan.io).

This repository stores agent definitions as JSON files. **GitHub is the database**- submitting an agent means opening a pull request, and merging it publishes the agent.

## How It Works

1. Browse agents at [zihin.io](https://zihin.io)
2. Click **"Download for izan.io"** to get the agent file
3. Import it in izan.io via **Settings → Agents → Import from File**
4. MCP servers are auto-configured during import

## Submit Your Agent

1. Go to [zihin.io/submit](https://zihin.io/submit)
2. Sign in with GitHub
3. Fill in your agent details (name, system prompt, MCP servers, etc.)
4. Submit- a pull request is created automatically
5. Once reviewed and merged, your agent is live

Or manually: fork this repo, add your agent under `agents/your-agent-slug/agent.json`, and open a PR.

## Repository Structure

```
agents/
  index.json                 # Auto-generated summary of all agents
  example-agent/
    agent.json               # Full agent definition
  your-agent/
    agent.json
```

## Agent Schema

Each `agent.json` follows this structure:

```json
{
  "schemaVersion": 1,
  "agent": {
    "id": "my-agent",
    "slug": "my-agent",
    "name": "My Agent",
    "description": "What this agent does",
    "icon": "🤖",
    "basePrompt": "You are an expert at...",
    "category": "Development",
    "author": {
      "githubUsername": "your-username",
      "displayName": "Your Name",
      "avatarUrl": "https://avatars.githubusercontent.com/u/your-username"
    },
    "version": "1.0.0",
    "tags": ["tag1", "tag2"],
    "createdAt": "2026-01-01T00:00:00.000Z",
    "updatedAt": "2026-01-01T00:00:00.000Z",
    "examplePrompts": [
      "Example question 1",
      "Example question 2"
    ],
    "requiredMCPs": [
      {
        "name": "My MCP Server",
        "url": "https://mcp.example.com/sse",
        "description": "What this server provides"
      }
    ]
  }
}
```

### Categories

`Development` · `Writing` · `Marketing` · `Data` · `Design` · `Productivity` · `Education` · `Finance` · `Other`

### Required MCP Servers

Agents can specify MCP (Model Context Protocol) servers they need. When a user downloads the agent and imports it into izan.io, these servers are automatically added to their configuration.

```json
"requiredMCPs": [
  {
    "name": "Server Name",
    "url": "https://your-mcp-server.com/sse",
    "description": "What tools this server provides"
  }
]
```

## Automation

When a PR is merged to `main` that modifies any `agents/*/agent.json` file, a GitHub Action automatically regenerates `agents/index.json`.

## License

AGPL-3.0- Same as [izan.io](https://github.com/nicepkg/izan.io)
