# ❗❗❗ DEPRECATION NOTICE ❗❗❗

# This action has been deprecated in favor of the [offical Pantheon Systems action for `terminus`](https://github.com/pantheon-systems/terminus-github-actions). On December 1st 2022, this repo will be archived (set to read-only).

# Setup Pantheon Terminus :zap:

A Github Action for quickly installing and configuring the Pantheon CLI tool, [Terminus](https://github.com/pantheon-systems/terminus).

## Requirements

- [Pantheon](https://pantheon.io) Account + Site
- [Pantheon Machine Token](https://pantheon.io/docs/machine-tokens)

## Usage

Using this action requires only calling within a workflow.

### Workflow Example

The following is a Github Workflow example which run `setup-pantheon-terminus`, then login to Pantheon via a machine token.

```yaml
name: Setup Terminus

on:
  push:
    branches:
    - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3

    - name: Setup Terminus
      uses: kopepasah/setup-pantheon-terminus@2

    - name: Login to Pantheon
      run: terminus auth:login -q --machine-token=${{ secrets.PANTHEON_MACHINE_TOKEN }}

    - name: List Sites
      if: success()
      run: terminus site:list
```

In the above example, `PANTHEON_MACHINE_TOKEN` is an encrypted secret added to the repo on Github, of which the value is the Machine Token generated by Pantheon.

## License

[Mozilla Public License 2.0](LICENSE)
