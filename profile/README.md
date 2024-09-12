## compat-fork

Sometimes there is a perfectly good package you want to use on [PyPI](https://pypi.org/)...
but it has some minor issue that makes it not work in a recent Python version, or an
incompatibility with some other library. It's easy to fix, but the original author isn't
around any more or is too busy to update the package.

That's where the compat-fork organization comes in. This organization provides a home
to keep these abandoned packages alive—or at least alive enough that they will keep
working.

We accept Python packages that already exist, but need some (hopefully small) updates
to keep them working in the current Python ecosystem. We don't do feature development
on these packages, just compatibility fixes and other tweaks to keep the code working
as the Python ecosystem evolves.

This organization isn't a place to develop new features. If you want to breathe new life
into one of the libraries and extend it with new features, please create your own fork
providing these features.

### What kind of packages are accepted?

- Python packages (not necessarily written in Python; we'll take extension modules)
- Not being maintained
- Has some issue that prevents you from using the package in the way you'd like to use it

### What kind of changes are accepted?

- Fixes for compatibility with newer Python versions
- Fixes for compatibility with newer packaging standards
- Fixes for compatibility with other libraries (e.g., removing version bounds)
- Improvements to the CI setup (e.g., migrating to Trusted Publishing and GitHub Actions)
- Changes to make it easier to release new versions
- Possibly other critical bug fixes (e.g., plugging security holes)
- Documentation changes pointing to alternative libraries that are still being maintained
  and provide similar functionality

### What kind of changes are *not* accepted?

- New features
- Large rewrites
- New documentation

### How do I propose a package for inclusion?

- [Open an issue](https://github.com/compat-fork/.github/issues/new) on this repo,
  with the name of the package and evidence it needs to be forked. Ideally, this should
  be a link to an issue on the original package's repository.
- We'll create the repo.
- Send PRs with fixes.
- We'll make a release to PyPI.

### Who is doing this?

This project was started by me (@JelleZijlstra) to solve some problems I ran into personally.
But a project that serves as insurance against abandoned packages really needs more than one
maintainer, so if you're interested in joining, please let me know.
