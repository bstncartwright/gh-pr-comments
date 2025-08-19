# gh-pr-comments

`gh-pr-comments` is a tiny GitHub CLI extension that outputs pull request review comments in markdown or a compact simple format. useful for generating PR comment summaries or embedding comment lists in markdown docs.

## installation

install via the official gh extensions mechanism (preferred):

```bash
gh extension install bstncartwright/gh-pr-comments
```

or install manually (not recommended):

```bash
cp gh-pr-comments $(git --exec-path)/gh-pr-comments
chmod +x $(git --exec-path)/gh-pr-comments
```

## usage

```bash
gh pr-comments [options] [<org/repo> <pr_number>]
```

options:
- `-h, --help`    show help
- `-f, --format`  output format: `markdown` (default) or `simple`

examples:
- `gh pr-comments`                             # uses current PR in repo
- `gh pr-comments cli/cli 3192`       # fetch for specific repo/pr
- `gh pr-comments --format simple`             # compact/simple output

## output

- markdown format prints a top-level heading with the repo and PR number, followed by sections for each comment (line, username, body) separated by `---`.
- simple format prints a more compact, human-readable list.

## behavior

- with no arguments the extension calls:

```
gh pr view --json number,headRepository,headRepositoryOwner
```

to determine the current PR and repository, then uses the REST API to fetch PR review comments.

- with two arguments the first should be `org/repo` and the second the PR number.

## requirements

- gh (GitHub CLI) >= 2.x
- jq

## troubleshooting

- if `gh pr view` fails, ensure you're in a git repo with a checked-out branch that has an associated PR and that `gh` is authenticated.
- if comments are missing, ensure the PR number and repo are correct and that you have permission to view the repository.

## license

MIT
