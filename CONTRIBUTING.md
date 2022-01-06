# Contributing

## Building

Dependencies:

- Python, at least version 3.5
- The `pybase16` command from
  [base16-builder-python](https://github.com/InspectorMustache/base16-builder-python)
- The `make` command

For example on a Debian-based distribution:

```
# Install dependencies (you probably already have pip/pip3 and make)
apt install build-essential # for make
pip3 install pybase16-builder

# Build the packages
make
```

## Submitting a PR

After you've installed the build dependencies, and before you submit your PR:

- Run `make` after you've made your changes. This will build all the themes
  based on the changes you've made. For instance, instead of manually editing
  files under `colors/`, you should edit `templates/default.mustache`
- Make sure to commit the changes from `make` and include them in your PR.
- Please abide by what's requested in the [PR
  template](/.github/pull_request_template.md).

## Submitting an issue

Please follow the instructions in the issue templates:

- [Issue template for bug reports](/.github/ISSUE_TEMPLATE/bug_report.md)
- [Issue template for feature requests](/.github/ISSUE_TEMPLATE/feature_request.md)
