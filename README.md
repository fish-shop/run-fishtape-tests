<img alt="fish" src="images/fish-market.png" width="160" align="right">

# fish-shop/run-fishtape-tests

[![Tests](https://img.shields.io/github/actions/workflow/status/fish-shop/run-fishtape-tests/test.yml?branch=main&color=brightgreen&label=tests)](https://github.com/fish-shop/run-fishtape-tests/actions) [![Issues](https://img.shields.io/github/issues/fish-shop/run-fishtape-tests)](https://github.com/fish-shop/run-fishtape-tests/issues) [![Dependabot](https://img.shields.io/badge/dependabot-active-brightgreen.svg)](https://github.com/fish-shop/run-fishtape-tests/network/dependencies) [![License](https://img.shields.io/badge/license-MIT-blue)](https://opensource.org/licenses/mit-license.php) [![fish](https://img.shields.io/badge/fish-3.2.2-blue)](https://fishshell.com)

A GitHub action for running [Fishtape](https://github.com/jorgebucaran/fishtape) tests.

<hr>

Here's an example from the test workflow for [Pond](https://github.com/marcransome/pond):

<img src="example.png">

## Prerequisites

This action requires the [fish shell](https://fishshell.com). You can install it using the [fish-actions/install-fish](https://github.com/fish-actions/install-fish) action.

## Usage

Add a suitable `uses` step to your GitHub [workflow](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions) as shown below:

```yaml
- name: Run Fishtape tests
  uses: fish-shop/run-fishtape-tests@v1
```

By default, all files under `$GITHUB_WORKSPACE` with a `.fish` file extension are recursively tested. To specify a different file pattern to match against, provide a value for the `pattern` input. For example, to check all `.fish` files starting in the `tests` directory and descending into subdirectories:

```yaml
- name: Run Fishtape tests
  uses: fish-shop/run-fishtape-tests@v1
  with:
    pattern: tests/**.fish
```

Multiple space-separated `pattern` values are supported and can include [wildcards](https://fishshell.com/docs/current/language.html#expand-wildcard) and [brace expansion](https://fishshell.com/docs/current/language.html?highlight=brace+expansion#brace-expansion):

```yaml
- name: Run Fishtape tests
  uses: fish-shop/run-fishtape-tests@v1
  with:
    pattern: tests/*.fish fixtures/**.fish {dir1,dir2}/**.fish ???-*.fish
```

By default, TAP output is piped to [tap-diff](https://github.com/axross/tap-diff) for improved readability. To disable this functionality and produce raw TAP output set `raw-output` to `'true'`:

```yaml
- name: Run Fishtape tests (raw TAP output)
  uses: fish-shop/run-fishtape-tests@v1
  with:
    pattern: tests/**.fish
    raw-output: 'true'
```

## Action versions

Use one of the following patterns when specifying the version reference for this action in your workflow (i.e. the `{ref}` value in `uses: fish-shop/run-fishtape-tests@{ref}`):

| Pattern  | Example   | Description                                                            |
|----------|-----------|------------------------------------------------------------------------|
| `vX`     | `v1`      | the latest `v1.*` release including non-breaking changes and bug fixes |
| `vX.Y`   | `v1.1`    | the latest `v1.1.*` release including bug fixes                        |
| `vX.Y.Z` | `v1.1.0`  | the `v1.1.0` release only                                      |                

> [!TIP]
> The recommended pattern is `vX` (e.g. `v1`). This will ensure that the version of the action used in your workflow includes the latest non-breaking changes and bug fixes, and guarantees compatibility with previous versions of that major release number.

Using a `main` branch reference in your workflow is _not_ recommended as this branch may include breaking changes intended for the next major release.

## Other GitHub actions

A number of related composite actions are also available from the [fish-shop](https://github.com/fish-shop) 🐟. Check them out:

* [fish-shop/install-fish-shell](https://github.com/fish-shop/install-fish-shell) - A GitHub action for installing fish shell
* [fish-shop/install-plugin](https://github.com/fish-shop/install-plugin) - A GitHub action for installing fish shell plugins
* [fish-shop/install-plugin-manager](https://github.com/fish-shop/install-plugin-manager) - A GitHub action for installing a fish shell plugin manager
* [fish-shop/syntax-check](https://github.com/fish-shop/syntax-check) - A GitHub action for syntax checking fish shell files

## Acknowledgements

 * Fish market icon made by [Freepik](https://www.flaticon.com/authors/freepik) from [www.flaticon.com](https://www.flaticon.com/)

## License
`fish-shop/run-fishtape-tests` is provided under the terms of the [MIT License](https://opensource.org/licenses/mit-license.php).

## Contact
Email me at [marc.ransome@fidgetbox.co.uk](mailto:marc.ransome@fidgetbox.co.uk) or [create an issue](https://github.com/fish-shop/run-fishtape-tests/issues).
