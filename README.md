# Undeployed Commits Action

A GitHub Action that lists commits on your main branch that haven't been deployed to production yet.

## Usage

The action runs manually via workflow dispatch:

1. Go to **Actions** tab in your repository
2. Select **undeployed-commits** workflow
3. Click **Run workflow**

## How It Works

The workflow uses the GitHub API to:

1. **Find the last successful production deployment** - Queries the Deployments API for your `prod` environment and checks each deployment's status to find the most recent successful one.

2. **Compare commits** - Uses the Compare API to find all commits between the last deployed SHA and the current HEAD.

3. **Filter and format output** - Excludes merge commits and displays each undeployed commit with its short SHA, message, and author.

### Example Output

```
Last production deployment: 2fbfbea
Current HEAD: a4f546d

Commits not yet deployed to production:
=========================================
• 8814f23 - Add user authentication (alice)
• 51c22ef - Fix dashboard loading bug (bob)
```

## Requirements

- Your repository must use **GitHub Environments** with a `prod` environment for production deployments
- This won't work if you cherry-pick commits for deployment to `prod`

demo1
demo2
demo3
