# commit-body-check

A GitHub Action that verifies wheather commits have bodys


## Dependencies
GitHub Action Tim-Zhang/get-pr-commits

## Usage
Add .github/workflows/sanity-check.yml with the following:

```
name: Sanity check
on: [pull_request]

jobs:
  commits_check_job:
    runs-on: ubuntu-latest
    name: Commits Check
    steps:
    - name: Get PR Commits
      id: 'get-pr-commits'
      uses: Tim-Zhang/get-pr-commits@master
      with:
        token: ${{ secrets.GITHUB_TOKEN }}
    - name: Commit Body Check
      uses: Tim-Zhang/commit-body-check@master
      with:
        commits: ${{ steps.get-pr-commits.outputs.commits }

```
