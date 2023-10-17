# setup-anybody

[![CI](https://github.com/anybody/setup-anybody/actions/workflows/test.yml/badge.svg)](https://github.com/anybody/setup-anybody/actions/workflows/test.yml)

GitHub Action to setup the console version the [AnyBody Modeling System](https://anybodytech.com) on Windows based GitHub actions runners.

For similar actions for linux machines, please see [anybodycon-action](https://github.com/AnyBody/anybodycon-action), or the [AnyBody docker containers](https://github.com/AnyBody/anybody-container/pkgs/container/anybodycon).


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

The `anybodycon.exe` application is installed under `$HOME` directory (e.g. `C:\Users\runneradmin\AnyBody Technology\AnyBody.7.5`).
The folder is added to path so `AnyBodyCon.exe` can be called directly.

The available inputs options are:

#### anybody-version (Required)
   The version of AnyBody to install. E.g. `7.5.0`.

#### anybody-version_suffix (optional)
    Suffix for special versions. E.g. "Beta"

#### python-environment (optional)
    The python environment use by the AnyBody Python hooks. Possible options are `full`, `minimal` (default), `none`, or `<custom-env-file>.yaml`. 
    The `full` option is identical to the python environment shipped with the standard version of AnyBody. The `minimal` option only installs Python. 
    Select 'none' to speed things up if your models don't use the AnyBody Python hooks. It is also possible to specify a custom environment file.


# AnyBody license server

A valid license for AnyBody is required when running the version of AnyBody
installed by this action. The license can be provided by setting two environment
variables: `RLM_LICENSE` and `RLM_LICENSE_PASSWORD`. The values of these
variables should be set to the license server address and password respectively.


It is recommended to keep these values secret and add them in the GitHub
repository settings under "Secrets".



