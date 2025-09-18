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

## Triggering the Workflow

The workflow runs on:
- Push to any branch
- Pull request creation/updates
- Manual trigger via workflow_dispatch

You can view the workflow runs in the Actions tab to see the matrix behavior in action.


Example changes. 
