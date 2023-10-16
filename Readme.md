# setup-anybody

[![CI](https://github.com/anybody/setup-anybody/actions/workflows/test.yml/badge.svg)](https://github.com/anybody/setup-anybody/actions/workflows/test.yml)

GitHub Action to setup the console version the [AnyBody Modeling System](https://anybodytech.com) on Windows based GitHub actions runners.

For similar actions for linux machines, please see [anybodycon-action](https://github.com/AnyBody/anybodycon-action), or the [AnyBody docker containers}(https://github.com/AnyBody/anybody-container/pkgs/container/anybodycon).


## Usage

```yml
- uses: anybody/setup-anybody@main
  with:
    anybody-version: '7.5.0'
    python-environment: "full"

- name: Run AnyBodyCon
    run: |
        anybodycon /ni
    env:
        RLM_LICENSE: ${{ secrets.RLM_LICENSE }}
        RLM_LICENSE_PASSWORD: ${{ secrets.RLM_LICENSE_PASSWORD }}
    
```

## Features

The available inputs are:

* **anybody-version**: The version of AnyBody to install. E.g. `7.5.0`.
* **anybody-version_suffix**: Suffix for special versions. E.g. "Beta"
* **python-environment**: The python environment to install. E.g. `full` or `minimal`, `None`. Default: `None`.

The `python-environment` input can also specify a "environment.yml" file to install a custom python environment.

# AnyBody license server

A valid license for AnyBody is required when running the version of AnyBody
installed by this action. The license can be provided by setting two environment
variables: `RLM_LICENSE` and `RLM_LICENSE_PASSWORD`. The values of these
variables should be set to the license server address and password respectively.
It is recommended to keep these values secret and add them in the GitHub
repository settings under "Secrets".



