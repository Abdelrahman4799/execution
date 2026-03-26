# Enspct Test Automation - Setup Guide

## Prerequisites
- [Node.js](https://nodejs.org/) (v18 or later)
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI installed

## Step 1: Install Claude Code

If you haven't installed Claude Code yet:

```bash
npm install -g @anthropic-ai/claude-code
```

Verify installation:
```bash
claude --version
```

## Step 2: Configure Playwright MCP Server

The Playwright MCP server allows Claude Code to control a real browser. You need to add it to your Claude Code configuration.

### Option A: Via Claude Code CLI

Run this command in your terminal:

```bash
claude mcp add playwright -- npx @anthropic-ai/mcp-server-playwright
```

### Option B: Manual Configuration

1. Open your Claude Code config file:
   - **Windows:** `%USERPROFILE%\.claude.json`
   - **Mac/Linux:** `~/.claude.json`

2. Add the Playwright MCP server under `mcpServers`:

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@anthropic-ai/mcp-server-playwright"]
    }
  }
}
```

> If the file already has other MCP servers, just add the `"playwright"` entry inside the existing `"mcpServers"` object.

## Step 3: Verify MCP Server

1. Open a terminal in this project folder
2. Run Claude Code:
   ```bash
   claude
   ```
3. You should see `playwright` listed as a connected MCP server on startup
4. Test it by asking: `open google.com in the browser`

If the browser opens, you're all set.

## Step 4: Run Test Cases

1. Open this folder in your terminal
2. Start Claude Code:
   ```bash
   claude
   ```
3. Ask Claude to run tests:
   ```
   run the first test case in the csv file
   ```
   ```
   run test cases 1-5 from Enspct_Build Request Type Form.csv
   ```
   ```
   run all test cases
   ```

Results will be appended to `test-report.md` automatically.

## Troubleshooting

### "playwright" MCP server not connecting
- Make sure Node.js is installed: `node --version`
- Try installing the package globally: `npm install -g @anthropic-ai/mcp-server-playwright`
- Restart Claude Code after changing the config

### Browser not opening
- Ensure no firewall is blocking Chromium
- Try running `npx playwright install chromium` to install the browser binary

### Permission prompts on every action
- The `.claude/settings.local.json` file in this project pre-approves all Playwright tools
- If you're still getting prompts, restart Claude Code from this project folder
