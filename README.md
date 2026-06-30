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

## Install tetherscript

Install the published tetherscript compiler/runner from crates.io:

```sh
cargo install tetherscript --version 0.1.0-alpha.19
```

Confirm it is available on your `PATH`:

```sh
tetherscript --help
```

If Cargo's bin directory is not on your `PATH`, add it first.

Windows PowerShell:

```powershell
$env:PATH += ";$env:USERPROFILE\.cargo\bin"
```

macOS/Linux shell:

```sh
export PATH="$HOME/.cargo/bin:$PATH"
```

## Compile this CLI

From this repository root, compile the tetherscript source into a standalone binary.

Windows:

```powershell
tetherscript build src/forgejo_cli.tether -o forgejo-cli.exe
```

macOS/Linux:

```sh
tetherscript build src/forgejo_cli.tether -o forgejo-cli
```

Exact command used during local validation from the adjacent tetherscript source checkout:

```powershell
cargo run --quiet --manifest-path ../tetherscript/Cargo.toml -- build src/forgejo_cli.tether -o forgejo-cli.exe
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
