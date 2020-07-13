# Contributing to this project

This is an open source project, and we welcome contributions of all kinds.

* By contributing, you agree that we may redistribute your work under the [GPLv2.0](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html) license.
* Everyone involved in this project agrees to abide by [Contributor Covenant Code of Conduct v1.4](https://www.contributor-covenant.org/version/1/4/code-of-conduct.html).

## Submitting bug reports

Ensure that you're running the latest stable version of this software. Submit a new issue with the bug report, ensure that it includes enough information to reproduce the problem. Include target platform, version and version of relevant libraries.

## Contributing code

* Contributions are managed via GitHub pull requests, usually as a response for an issue.
* Pull requests should contain the template below, where you tick off that you agree to license and code of conduct.
* Contributors will be listed in [CONTRIBUTORS.md](CONTRIBUTORS.md).

### Pull request template

```
Hi!

I'd like to contribute [feature|bugfix|documentation].

[Description]

I confirm that my contributions will be compatible with the GPLv2.0 license guidelines.

* [ ] I have read and accepted both license and code of conduct.
* [ ] I have previously accepted and still accept both license and code of conduct.
```

## Development guidelines

### Ansible

* Follow [MET Ansible Style Guide v1.0.0](https://github.com/metno/ansible-styleguide).
* Testing of the role must work with free operating systems; operating systems without license cost.
* Documentation must be updated with the to reflect code and versioning.
* New features should be implemented for all operating systems a role supports.
* Changes to a feature should be implemented for all operating systems the role supports.
* Commits should be granular enough for others to understand and review.
* Commits should be descriptive and contain reference to issue number if it exists, e.g. #1234.

<!---
# vim: set spell spelllang=en:
-->
