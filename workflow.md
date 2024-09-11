# Default workflow for adding a new project to compat-fork

- Fork the project's GitHub repository into the compat-fork org
- Update the README to add a header saying this is a compat fork
  - Example text: https://github.com/compat-fork/diagrams/pull/1/files
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
