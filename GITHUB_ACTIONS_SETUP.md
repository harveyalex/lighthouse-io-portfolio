# GitHub Actions Automation Setup Guide

This guide explains how to set up automated weekly report generation using GitHub Actions.

## Prerequisites

1. Your code must be in a GitHub repository
2. Admin access to the repository settings
3. Azure DevOps credentials (Organization, Project, Personal Access Token)

## Setup Instructions

### Step 1: Add Secrets to GitHub

Go to your repository settings and add the following secrets:

**Settings → Secrets and variables → Actions → New repository secret**

Create these secrets:
- `AZURE_DEVOPS_PAT`: Your Azure DevOps Personal Access Token
- `AZURE_DEVOPS_ORG`: Your Azure DevOps Organization name
- `AZURE_DEVOPS_PROJECT`: Your Azure DevOps Project name

### Step 2: Upload Files to Repository

Ensure these files are in your repository:
```
.github/workflows/weekly-reports.yml    # Workflow definition
requirements.txt                         # Python dependencies
fetch_workitems.py                      # Work items fetcher
generate_reports.py                     # Analytics generator
generate_enriched_analytics.py           # Enriched analytics
generate_release_notes.py                # Release notes generator
prs-enhanced.md                          # PR data (input)
```

### Step 3: Test the Workflow

1. Push changes to your main branch
2. Go to **Actions** tab in your repository
3. Click on "Weekly Report Generation"
4. Click **Run workflow** → **Run workflow** button

## Workflow Details

### Schedule
- Runs automatically every **Monday at 8:00 AM UTC**
- Can be manually triggered via workflow dispatch

### What It Does
1. Fetches latest work items from Azure DevOps
2. Generates analytics reports
3. Creates enriched analytics combining PR and work item data
4. Updates release notes
5. Commits and pushes changes automatically

### Workflow Status

The workflow will:
- ✅ Create a commit with timestamp: `chore: auto-generate weekly reports YYYY-MM-DD`
- ✅ Push changes to your current branch
- ✅ Post summary to workflow run

### Environment Variables

The workflow uses these secrets from GitHub:
```yaml
AZURE_DEVOPS_PAT: Your Personal Access Token
AZURE_DEVOPS_ORG: Organization name
AZURE_DEVOPS_PROJECT: Project name
```

## Customization

### Change Schedule
Edit `.github/workflows/weekly-reports.yml`:
```yaml
on:
  schedule:
    - cron: '0 8 * * 1'  # Monday 8 AM UTC
```

**Cron Format**: `minute hour day month day-of-week`

Common schedules:
- Daily at 9 AM: `0 9 * * *`
- Fridays at 5 PM: `0 17 * * 5`
- Every 6 hours: `0 */6 * * *`

### Additional Steps
Add more generators to `generate-reports` step:
```yaml
run: |
  python3 your_custom_script.py
```

## Troubleshooting

### Workflow fails with authentication error
- ✓ Verify `AZURE_DEVOPS_PAT` is correct
- ✓ Check PAT has required scopes (Work Items, Code)
- ✓ Ensure `AZURE_DEVOPS_ORG` and `AZURE_DEVOPS_PROJECT` are correct

### Workflow fails with "file not found"
- ✓ Ensure all Python scripts are in repository root
- ✓ Check requirements.txt exists
- ✓ Verify `prs-enhanced.md` exists

### Changes not being pushed
- ✓ Ensure GitHub token has push permissions (default)
- ✓ Check branch protection rules don't block automation
- ✓ Verify no authentication issues in logs

## Manual Execution

To run the workflow manually:
1. Go to **Actions** tab
2. Select "Weekly Report Generation"
3. Click **Run workflow** dropdown
4. Select branch and click **Run workflow**

## Monitoring

View workflow runs:
1. Go to **Actions** tab
2. Click "Weekly Report Generation"
3. See all runs with status and duration
4. Click individual runs for detailed logs

## Environment Variables

These are set by the workflow from GitHub secrets:
```
AZURE_DEVOPS_PAT        # From GitHub secret
AZURE_DEVOPS_ORG        # From GitHub secret
AZURE_DEVOPS_PROJECT    # From GitHub secret
```

The scripts read these and authenticate with Azure DevOps API.

## Security Notes

- ✅ PAT is never exposed in logs (marked as secret)
- ✅ Only commits authored by "GitHub Action"
- ✅ Changes are reviewed in commit history
- ✅ Secrets are encrypted by GitHub

## Next Steps

1. Push all files to GitHub
2. Add required secrets in repository settings
3. Test workflow by running manually
4. Verify reports are generated and pushed
5. Set up branch notification for automated commits

---

**For questions or issues**: Check workflow logs under Actions → Workflow runs
