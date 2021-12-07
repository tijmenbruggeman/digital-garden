---
title: "Github"
tags: ['git', 'github', 'cli']
---


## Often used
### Install Github CLI
```bash
# on windows
winget install --id=GitHub.cli -e

# on mac

```

### Quickly create a repository
```bash
gh repo create <name>

# --public/--private/--internal to use non-interactive
# --disable-issues Disable issues in the new repository
# --disable-wiki Disable issues in the new repository
# --push Push local commits to the new repository

# Example:
gh repo create example-repo --public --push --disable-issues --disable-wiki
```

## Resources
https://cli.github.com/manual