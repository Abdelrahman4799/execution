# Enspct Test Automation Project

## Overview
Automated E2E testing for the **Enspct** inspection platform using Claude Code with Playwright MCP browser tools. Test cases are defined in CSV files exported from Azure DevOps.

## How It Works
1. Place your CSV test case file(s) in this folder
2. The `.env` file is already configured with shared credentials
3. Ask Claude to run test cases from your CSV file
4. Results are appended to `test-report.md`

## Prerequisites
- **Claude Code** CLI installed
- **Playwright MCP server** configured in Claude Code settings (see Setup below)

## Setup

### 1. Configure Playwright MCP Server
Add the following to your Claude Code MCP settings (`~/.claude.json` or via Claude Code settings):
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

### 2. Environment Variables
The `.env` file is included in the project with shared team credentials. No changes needed.

### 3. Permissions
The `.claude/settings.local.json` file pre-approves the necessary Playwright MCP tools so you don't have to approve each action manually.

## Execution Rules
- Tests run **headed** (visible browser) via Playwright MCP tools — no scripts are generated
- **No screenshots** are taken unless a test step fails
- Keep the project folder clean — only CSV files, `.env`, and `test-report.md` should persist
- All test results are appended to `test-report.md` after each run

## Test Report
`test-report.md` is a cumulative report. Each test case result is appended with:
- Summary row in the results table
- Detailed steps, expected vs actual results
- Failure screenshots (only when applicable)

## App Navigation Reference
- **Login:** Navigate to BASE_URL, switch to English if needed, login with credentials
- **Admin role** is required for Form Builder / Request Types tests
- **Path to Request Types:** Builders menu > Request Types
- **Path to Form Builder:** Click the Build Form icon on any request type row
- Static fields use Arabic labels: **المنشأة** (Entity), **الموقع** (Location)

## CSV File Format
CSV files are exported from Azure DevOps with columns:
`ID, Work Item Type, Title, Test Step, Step Action, Step Expected, Area Path, Assigned To, State`

## Example Commands
```
> run the first test case in the csv file
> run test cases 1-5 from Enspct_Build Request Type Form.csv
> run all test cases
```
