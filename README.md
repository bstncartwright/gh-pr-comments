# gh-pr-comments

`gh-pr-comments` is a small GitHub CLI extension that prints pull request review comments in markdown (or a simple) format.

## installation

copy the `gh-pr-comments` file from this extension directory into a directory on your PATH and mark it executable, or use the gh extensions mechanism:

# install locally
cp gh-pr-comments $(git --exec-path)/gh-pr-comments
chmod +x $(git --exec-path)/gh-pr-comments

## usage

Usage: gh pr-comments [options] [<org/repo> <pr_number>]

Options:
- `-h, --help` Show help
- `-f, --format FORMAT` Output format (`markdown`, `simple`). Default: `markdown`

Examples:
- `gh pr-comments`                    # Use current PR
- `gh pr-comments PrinterLogic/vac 3192`
- `gh pr-comments --format simple`    # Simpler output format

## behavior

- when run with no arguments the extension calls `gh pr view --json number,headRepository,headRepositoryOwner` to determine the current PR number and repository and then fetches PR review comments via the GitHub API.
- when run with two arguments, the first is `org/repo` and the second is the PR number.

## requirements

- gh (GitHub CLI)
- jq

## license

MIT
