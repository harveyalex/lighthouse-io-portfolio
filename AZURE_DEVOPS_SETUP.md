# Azure DevOps MCP Setup Guide

## Overview
This guide will help you set up the official Microsoft Azure DevOps MCP server for OpenCode integration.

## Prerequisites
- Node.js 20+ installed
- Azure DevOps Personal Access Token (PAT)

## Step 1: Create Your Azure DevOps Personal Access Token

To get your PAT:

1. Navigate to https://dev.azure.com/teamsoftwareinc/
2. Click your profile icon in the top right → Personal access tokens
3. Click "New Token"
4. Configure:
   - **Name:** OpenCode Integration
   - **Organization:** teamsoftwareinc
   - **Expiration:** Select appropriate expiration (180 days is typical)
   - **Scopes:** Select "Full access" or at minimum these scopes:
     - Code (Read)
     - Work Items (Read & Write)
     - Build (Read)
     - Notifications (Read)
     - Wiki (Read)
     - Project & Team (Read)
5. Click "Create" and **copy your token immediately** (you won't see it again)

## Step 2: Set Environment Variable

Add your PAT to your shell configuration file:

```bash
# Add to ~/.zshrc or ~/.bashrc or ~/.zshenv
export AZURE_DEVOPS_PAT="your_pat_token_here"
```

Then reload your shell:
```bash
source ~/.zshrc  # or ~/.bashrc
```

## Step 3: Update OpenCode Config

Copy the configuration from `opencode.json` in this directory to your OpenCode config:

```bash
cp /Users/alexharvey/development/opencode.json ~/.config/opencode/opencode.json
```

The configuration will use your `AZURE_DEVOPS_PAT` environment variable automatically.

## Step 4: Restart OpenCode

Restart OpenCode to load the new MCP server:

```bash
opencode
```

## Step 5: Test the Integration

Try these commands in OpenCode to verify it's working:

```
List my ADO projects
```

```
List ADO work items for project "Lighthouse-io"
```

## What You Can Do Now

With the Azure DevOps MCP configured, you can:
- Query work items, projects, and teams
- Get build and pipeline information
- Access repository and pull request details
- Retrieve wiki content
- Search code, work items, and wikis

## Configuration Reference

The MCP server is configured with:
- **Organization:** teamsoftwareinc
- **Authentication:** Using `AZURE_DEVOPS_PAT` environment variable
- **Domains enabled:** All (core, work, work-items, repositories, pipelines, wiki, etc.)

## Next Steps

After setup, you can:
1. Enrich the PR documentation with Azure DevOps ticket details
2. Create automated reports linking PRs to work items
3. Query work item status directly from OpenCode

## Troubleshooting

### "Permission denied" errors
- Ensure your PAT has sufficient scopes (start with "Full access")
- Check that the organization name is correct: `teamsoftwareinc`

### "Tool not found" errors
- Ensure Node.js 20+ is installed
- Try running manually: `npx -y @azure-devops/mcp teamsoftwareinc`

### Authentication issues
- The MCP server will open a browser window on first use - ensure you're logging in with the correct Microsoft account
- Your PAT must be valid and not expired

For more help, see: https://github.com/microsoft/azure-devops-mcp/blob/main/docs/TROUBLESHOOTING.md
