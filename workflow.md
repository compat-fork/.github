# Default workflow for adding a new project to compat-fork

- Fork the project's GitHub repository into the compat-fork org
- Update the repo for the new project name
  - See template below for what to add to the README
  - Also update the `pyproject.toml` (or wherever the project keeps its config)
    to set the name to `compat-fork-<original name>` and update the
    package's URLs.
- Send a PR to make that README update. Use this PR to ensure CI runs correctly.
- Add a `publish.yml` to build the project using Trusted Publishing. Samples:
  - https://github.com/compat-fork/PyAPNs2/blob/master/.github/workflows/publish.yml (using `build`)
  - https://github.com/compat-fork/diagrams/blob/master/.github/workflows/publish.yml (using `poetry`)
- Make whatever changes you need to make to the repo (e.g., update
  Python version support)
- Go to https://pypi.org/manage/account/publishing/ and add Trusted Publishing
  for the new repo
- Update the repo to prepare a new release (update the version number, put
  a changelog in the README)
- Create a GitHub release, adding a tag matching the version you just added
- Monitor the GitHub Actions tab to make sure the release finishes successfully

# README template

```
# compat-fork-<NAME>

[![pypi version](https://badge.fury.io/py/compat-fork-<NAME>.svg)](https://badge.fury.io/py/compat-fork-<NAME>)

This is a fork of the [<NAME>](https://github.com/<OWNER>/<NAME>) library
to add compatibility fixes. It is part of the [compat-fork](https://github.com/compat-fork) project.

Compat-fork changelog:

- Version 0.0.0 (September 0, 2000)
  - Do something

---

Original README follows:
```

# Release workflow

The default workflow for releases on forks should be:

- File a PR updating the version number (probably in `pyproject.toml`)
  and changelog
- Create a GitHub release
- Let Trusted Publishing do its job

# Troubleshooting

- Make sure that the project name is updated to `compat-fork-X` where X is
  the original name.
  - Example change needed for Poetry: https://github.com/compat-fork/diagrams/pull/7/files
- To make sure Actions run, you may have to:
  - Go to the Actions tab and push some buttons
  - Rename the workflow file to something else. GitHub seems to block running
    workflows on forks if the name matches or something.

# Repo settings

Open to changing this to what makes sense for different repos,
but I like to set the following settings on each repo:

- Enable issues (disabled by default on forks)
- Allow only squash merges for PRs
- Always suggest updating PR branches
- Automatically delete head branches

# Versioning

Versioning should follow the spirit of the original library's
versioning policy. To mark a clean break, I like to increment at least
the minor version number (e.g., if the original library's release was
0.12.3, make the first compat-fork release 0.13.0).
