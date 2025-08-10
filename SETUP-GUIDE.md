# Keep Backend Alive

This repository contains scripts to keep your Render.com free tier backends alive by pinging them every 5 minutes using GitHub Actions.

## Quick Setup Guide

### For Backend 1:

1. Copy `keep-alive-backend1.py` and `.github/workflows/keep-alive-backend1.yml` to your **Backend 1 repository**
2. Edit `keep-alive-backend1.py` and replace the URL with your Backend 1's health endpoint
3. Commit and push to your Backend 1 repository
4. Go to your Backend 1 repository on GitHub → Actions tab → "Keep Backend Alive" → "Run workflow"

### For Backend 2:

1. Copy `keep-alive-backend2.py` and `.github/workflows/keep-alive-backend2.yml` to your **Backend 2 repository**
2. Edit `keep-alive-backend2.py` and replace the URL with your Backend 2's health endpoint
3. Commit and push to your Backend 2 repository
4. Go to your Backend 2 repository on GitHub → Actions tab → "Keep Backend 2 Alive" → "Run workflow"

## Files in this repository:

- `keep-alive-backend1.py` - Script for Backend 1
- `keep-alive-backend2.py` - Script for Backend 2
- `.github/workflows/keep-alive-backend1.yml` - GitHub Action for Backend 1
- `.github/workflows/keep-alive-backend2.yml` - GitHub Action for Backend 2
- `requirements.txt` - Python dependencies

## How it works:

1. **GitHub Actions Scheduler**: Runs every 5 minutes using cron (`*/5 * * * *`)
2. **Python Script**: Makes a GET request to your backend's health endpoint
3. **Logging**: Shows timestamp, response status, and any errors
4. **Manual Trigger**: You can also run the workflow manually from GitHub Actions

## Important Notes:

- Replace the URLs in both Python files with your actual backend URLs
- Make sure your backends have a health endpoint (like `/health`, `/ping`, etc.)
- GitHub Actions may have slight delays during high server load
- Free GitHub Actions has monthly limits, but this usage should be well within limits

## Setup Steps:

### Step 1: Prepare Backend 1

```bash
# In your Backend 1 repository root:
# 1. Copy keep-alive-backend1.py to root directory
# 2. Copy .github/workflows/keep-alive-backend1.yml to .github/workflows/
# 3. Edit the URL in keep-alive-backend1.py
# 4. Commit and push
```

### Step 2: Prepare Backend 2

```bash
# In your Backend 2 repository root:
# 1. Copy keep-alive-backend2.py to root directory
# 2. Copy .github/workflows/keep-alive-backend2.yml to .github/workflows/
# 3. Edit the URL in keep-alive-backend2.py
# 4. Commit and push
```

### Step 3: Enable Actions

1. Go to each repository on GitHub
2. Navigate to Actions tab
3. Find the "Keep Backend Alive" workflow
4. Click "Run workflow" to start it immediately
5. The workflow will then run automatically every 5 minutes

## Troubleshooting:

- Check the Actions tab for workflow run logs
- Ensure your backend health endpoint returns 200 status code
- Verify the URL is correct and accessible
- GitHub Actions may be delayed during peak times
