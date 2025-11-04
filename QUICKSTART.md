# Quick Reference - Azure DevOps MCP Setup

## 🚀 TL;DR Setup (5 minutes)

### 1. Get Your Personal Access Token
```bash
# Go to: https://dev.azure.com/teamsoftwareinc/_usersSettings/tokens
# Create token with "Full access" scope
# Copy your token
```

### 2. Set Environment Variable
```bash
# Add to ~/.zshrc or ~/.bashrc
export AZURE_DEVOPS_PAT="paste_your_token_here"

# Reload shell
source ~/.zshrc
```

### 3. Update OpenCode Config
```bash
cp /Users/alexharvey/development/opencode.json ~/.config/opencode/opencode.json
```

### 4. Restart OpenCode
```bash
opencode
```

### 5. Test It
In OpenCode, type:
```
List my ADO projects
```

---

## 📊 What You Now Have

| File | Purpose | Size |
|------|---------|------|
| `prs.md` | All 637 PRs listed | 94 KB |
| `prs-enhanced.md` | PRs with work item links | 177 KB |
| `workitem_queries.json` | 103 work item IDs for batch queries | 1.5 KB |
| `INDEX.md` | Complete documentation | 6.6 KB |
| `AZURE_DEVOPS_SETUP.md` | Detailed setup guide | 3 KB |
| `extract_workitems.py` | Python script for data extraction | 3.3 KB |

---

## 🎯 Key Statistics

```
Total PRs:                637
  - Merged:              456
  - Open:                 31
  - Closed:              150

PRs with work items:      228
Unique work items:        103
Repositories:             10+
```

---

## 🔍 Example Queries

Once set up, try these in OpenCode:

```
# List projects
"List my ADO projects"

# Get work item details
"Get work item AB#231429"

# Query work items
"List all work items for project Lighthouse-io"

# Find PRs
"List pull requests for project api"
```

---

## ⚙️ Configuration Details

**Configured Organization:** teamsoftwareinc
**Auth Method:** Personal Access Token (PAT)
**MCP Domains Enabled:** All
**MCP Version:** @azure-devops/mcp v2.2.1 (Microsoft Official)

---

## 🐛 Troubleshooting

| Problem | Solution |
|---------|----------|
| Tool not found | Ensure Node.js 20+ is installed |
| Permission denied | Check PAT has "Full access" scope |
| Can't find organization | Verify "teamsoftwareinc" is correct |
| Token expired | Create new PAT in Azure DevOps |

---

## 📚 Resources

- **Setup Guide:** `AZURE_DEVOPS_SETUP.md` (in this directory)
- **Full Docs:** `INDEX.md` (in this directory)
- **OpenCode Docs:** https://opencode.ai/docs/mcp-servers/
- **Azure DevOps MCP:** https://github.com/microsoft/azure-devops-mcp

---

## ✅ Verification Checklist

- [ ] PAT created and copied
- [ ] `AZURE_DEVOPS_PAT` environment variable set
- [ ] OpenCode config updated
- [ ] OpenCode restarted
- [ ] "List my ADO projects" query works
- [ ] Can query specific work items

---

**Status:** Ready for Azure DevOps Integration
**Created:** November 4, 2025
