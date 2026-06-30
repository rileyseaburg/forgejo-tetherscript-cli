# forgejo-tetherscript-cli

A small Forgejo API command-line client written in tetherscript for:

- Swagger UI: <https://forgejo.quantum-forge.io/api/swagger>
- API base: <https://forgejo.quantum-forge.io/api/v1>

## Commands

```text
forgejo-cli <command> [args]

global flags: --base <api-base> --token <token>
commands:
  version
  user
  repos <owner>
  repo <owner> <repo>
  issues <owner> <repo>
  get <api-path>
  post <api-path> <json-body>
```

## Build

From the tetherscript repository or anywhere `tetherscript` is on `PATH`:

```sh
tetherscript build src/forgejo_cli.tether -o forgejo-cli
```

On Windows from the tetherscript repository:

```sh
cargo run --quiet -- build ../forgejo-tetherscript-cli/src/forgejo_cli.tether -o ../forgejo-tetherscript-cli/forgejo-cli.exe
```

## Usage

```sh
./forgejo-cli version
./forgejo-cli repos some-owner
./forgejo-cli repo some-owner some-repo
./forgejo-cli issues some-owner some-repo
./forgejo-cli get /version
```

Authenticated endpoints can use either a flag or environment variable:

```sh
./forgejo-cli --token "$FORGEJO_TOKEN" user
FORGEJO_TOKEN=... ./forgejo-cli user
```

## Source

The CLI implementation lives in `src/forgejo_cli.tether`.
