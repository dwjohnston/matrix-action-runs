# Matrix Action Runs Demo

This repository demonstrates GitHub Actions matrix jobs with conditional failure.

## Workflow Overview

The GitHub Actions workflow (`.github/workflows/matrix-demo.yml`) creates a matrix of jobs with:

- **a**: `["foo", "bar"]`  
- **b**: `["quiz", "qax"]`

This creates 4 combinations:
1. `foo/quiz` ✅ (passes)
2. `foo/qax` ✅ (passes) 
3. `bar/quiz` ✅ (passes)
4. `bar/qax` ❌ (fails intentionally)

## Behavior

- Each matrix job echoes the pair values
- The `bar/qax` combination is designed to fail as a demonstration
- All other combinations should pass successfully
- A summary "check" job runs after all matrix jobs complete
- The check job succeeds only if ALL matrix jobs succeed
- Use the "check" job status for branch protection rules

## Triggering the Workflow

The workflow runs on:
- Push to any branch
- Pull request creation/updates
- Manual trigger via workflow_dispatch

You can view the workflow runs in the Actions tab to see the matrix behavior in action.

## Branch Protection

To prevent merging PRs when matrix jobs fail, configure your branch protection rules to require the **"check"** status check instead of individual matrix job status checks. The check job will only succeed when all matrix job combinations pass.

In your repository settings:
1. Go to Settings > Branches
2. Add or edit branch protection rules
3. Enable "Require status checks to pass before merging"
4. Select "check" from the list of status checks
5. Do NOT select individual matrix job status checks (e.g., "matrix-job (bar, qax)")

This gives you a single, reliable status check that represents the overall health of your matrix builds.