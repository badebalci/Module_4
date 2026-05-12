# AI Bootcamp - Day 4

This repository contains product documentation artifacts for an authentication feature and prompt-driven sync workflows for Jira and Confluence.

## What Is In This Project

- Product requirements in markdown
- User stories in markdown
- Reusable prompt files for:
  - Jira sync
  - Confluence sync
  - Two-way sync planning
  - Sync status checks
- VS Code MCP server configuration for Atlassian, Context7, and Playwright

## Project Structure

```text
.
├── .github/
│   └── prompts/
│       ├── check-sync-status.prompt.md
│       ├── sync-plan.prompt.md
│       ├── sync-to-confluence.prompt.md
│       └── sync-to-jira.prompt.md
├── .vscode/
│   └── mcp.json
└── specs/
    ├── prds/
    │   └── PRD-001.md
    └── stories/
        └── STORY-001.md
```

## Specification Files

- `specs/prds/PRD-001.md`: User Authentication PRD with functional and non-functional requirements
- `specs/stories/STORY-001.md`: User Login Form story with acceptance criteria and technical notes

Both files use YAML frontmatter and include sync metadata:

- `sync.jira` for Jira-linked documents
- `sync.confluence` for Confluence-linked documents
- `synced_at` for last successful sync timestamp

## Prompt Files

Prompt files live under `.github/prompts/`:

- `sync-to-jira.prompt.md`: Batch create/update story issues in Jira
- `sync-to-confluence.prompt.md`: Batch create/update PRDs in Confluence
- `sync-plan.prompt.md`: Build a two-way sync plan with conflict detection and approval gate
- `check-sync-status.prompt.md`: Report sync freshness, orphaned resources, and potential conflicts

## Prerequisites

- VS Code with Copilot Chat enabled
- Access to Atlassian workspace and resources used in frontmatter
- Node.js available in PATH (for `npx` MCP servers)
- Optional: Context7 API key configured via VS Code input prompt

## MCP Configuration

MCP server definitions are in `.vscode/mcp.json`:

- `com.atlassian/atlassian-mcp-server`
- `io.github.upstash/context7`
- `microsoft/playwright-mcp`

If a server fails to start, re-open VS Code and verify network/auth settings for that provider.

## Typical Workflow

1. Update spec files under `specs/`
2. Run sync status check using the status prompt
3. Generate a two-way sync plan
4. Review conflicts and approve actions
5. Execute sync and confirm `synced_at` updates

## Notes

- This repo is documentation-first and does not include application source code.
- Keep frontmatter sync fields accurate to avoid incorrect direction decisions in two-way sync.
