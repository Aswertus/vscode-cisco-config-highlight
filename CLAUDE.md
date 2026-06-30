# CLAUDE.md

This file provides guidance to Claude Code when working in this repository.

## Project

This is a fork of [Y-Ysss/vscode-cisco-config-highlight](https://github.com/Y-Ysss/vscode-cisco-config-highlight),
a VS Code extension for Cisco device configuration syntax highlighting. The fork lives at
`Aswertus/vscode-cisco-config-highlight` (remote `origin`); the original project is configured
as remote `upstream`.

## Syncing with upstream

`.github/workflows/sync-upstream.yml` runs daily (and via manual `workflow_dispatch`) and
fast-forwards `main` from `upstream/main`, pushing the result back to `origin/main`. This is
the primary sync mechanism — no manual action is normally needed.

If the workflow fails (it uses `git merge --ff-only`, so it fails loudly rather than creating
a merge commit), `main` likely has local commits that diverge from upstream. Resolve manually:

```sh
git remote add upstream https://github.com/Y-Ysss/vscode-cisco-config-highlight.git  # one-time setup
npm run sync-upstream   # fetch + checkout main + ff-only merge + push origin
```

If a true merge/rebase is needed instead of a fast-forward, run the steps from
`sync-upstream` individually and replace `git merge --ff-only upstream/main` with
`git merge upstream/main` (or `git rebase upstream/main` to keep history linear).
