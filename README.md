# zihin.io - Browser Tool Marketplace for izan.io

Community-driven marketplace for browser automation tools used with the [izan.io](https://izan.io) Chrome extension.

This repository stores tool definitions as JSON files. **GitHub is the database** - submitting a tool means opening a pull request, and merging it publishes the tool.

## How It Works

1. Browse tools at [zihin.io](https://zihin.io) or in the izan.io extension side panel (Store tab)
2. Click **Install** to add a tool to your extension
3. The tool is immediately available to any connected MCP client

## Submit a Tool

1. Go to [zihin.io/submit](https://zihin.io/submit)
2. Sign in with GitHub
3. Fill in your tool details (name, description, parameters, code)
4. Submit - a pull request is created automatically
5. Once reviewed and merged, your tool is live

Or manually: fork this repo, add your tool under `tools/your-tool-slug/tool.json`, and open a PR.

## Repository Structure

```
tools/
  index.json                 # Auto-generated summary of all tools
  get-page-title/
    tool.json                # Full tool definition
  your-tool/
    tool.json
```

## Tool Schema

Each `tool.json` follows this structure:

```json
{
  "schemaVersion": 1,
  "tool": {
    "id": "my-tool",
    "slug": "my-tool",
    "name": "my_tool",
    "displayName": "My Tool",
    "description": "What this tool does",
    "category": "Productivity",
    "author": {
      "githubUsername": "your-username",
      "displayName": "Your Name",
      "avatarUrl": "https://github.com/your-username.png"
    },
    "version": "1.0.0",
    "tags": ["tag1", "tag2"],
    "parameters": [
      {
        "name": "url",
        "type": "string",
        "description": "The URL to navigate to",
        "required": true
      }
    ],
    "code": "async (params, browser) => {\n  await browser.open(params.url)\n  await browser.waitForLoad()\n  const title = await browser.evaluate('document.title')\n  await browser.close()\n  return { title }\n}",
    "createdAt": "2026-01-01T00:00:00.000Z",
    "updatedAt": "2026-01-01T00:00:00.000Z"
  }
}
```

### Categories

`Social Media` · `Productivity` · `E-Commerce` · `Finance` · `Education` · `Entertainment` · `Travel` · `Development` · `Other`

### Browser API (available in tool code)

```javascript
browser.open(url)              // Open URL in new tab
browser.navigate(url)          // Navigate current tab
browser.click(selector)        // Click element
browser.type(selector, text)   // Type into input
browser.getText(selector)      // Get element text
browser.evaluate(expression)   // Run JS in page
browser.waitForSelector(sel)   // Wait for element
browser.waitForLoad()          // Wait for page load
browser.snapshot()             // Accessibility tree
browser.close()                // Close tab
```

## Automation

When a PR is merged to `main` that modifies any `tools/*/tool.json` file, a GitHub Action automatically regenerates `tools/index.json`.

## License

AGPL-3.0
