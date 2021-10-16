# `tap-stackexchange`

Singer tap for the StackExchange API.

Built with the [Meltano SDK](https://sdk.meltano.com) for Singer Taps and Targets.

## Capabilities

* `sync`
* `catalog`
* `state`
* `discover`

## Settings

| Setting   | Required | Default | Description |
|:----------|:--------:|:-------:|:------------|
| key       | False    | None    | Pass this to receive a higher request quota |
| site      | False    | stackoverflow.com | StackExchange site |
| tags      | False    | None    | Question tags |
| start_date| False    | None    | The earliest record date to sync |

A full list of supported settings and capabilities is available by running: `tap-stackexchange --about`

## Installation

```bash
pipx install git+https://github.com/edgarrmondragon/tap-stackexchange.git
```

### Source Authentication and Authorization

Register a [new application on Stack Apps](https://stackapps.com/apps/oauth/register) and copy the generated `key`.

## Usage

You can easily run `tap-stackexchange` by itself or in a pipeline using [Meltano](https://meltano.com/).

### Executing the Tap Directly

```bash
tap-stackexchange --version
tap-stackexchange --help
tap-stackexchange --config CONFIG --discover > ./catalog.json
```

### Initialize your Development Environment

```bash
pipx install poetry
poetry install
```

<!--
### Create and Run Tests

Create tests within the `tap_stackexchange/tests` subfolder and
  then run:

```bash
poetry run pytest
```

You can also test the `tap-stackexchange` CLI interface directly using `poetry run`:

```bash
poetry run tap-stackexchange --help
```
-->

### Testing with [Meltano](https://www.meltano.com)

_**Note:** This tap will work in any Singer environment and does not require Meltano.
Examples here are for convenience and to streamline end-to-end orchestration scenarios._

Your project comes with a custom `meltano.yml` project file already created. Open the `meltano.yml` and follow any _"TODO"_ items listed in
the file.

Next, install Meltano (if you haven't already) and any needed plugins:

```bash
# Install meltano
pipx install meltano
# Initialize meltano within this directory
cd tap-stackexchange
meltano install
```

Now you can test and orchestrate using Meltano:

```bash
# Test invocation:
meltano invoke tap-stackexchange --version

# OR run a test `elt` pipeline:
meltano elt tap-stackexchange target-sqlite --job_id=stackexchange-sqlite

# Runtime configuration
TAP_STACKEXCHANGE__LOAD_SCHEMA=dragon_ball_gt \
TAP_STACKEXCHANGE_SITE=anime \
TAP_STACKEXCHANGE_TAGS='["dragon-ball-gt"]' \
meltano elt tap-stackexchange target-sqlite
```

### SDK Dev Guide

See the [dev guide](https://sdk.meltano.com/en/latest/dev_guide.html) for more instructions on how to use the SDK to 
develop your own taps and targets.
