# Rust

## Tools

- `rustup`: rust installer and update manager
- `rustc`: rust compiler
- `cargo`: rust build system and package manager
- `cargo clippy`: rust code linter
- `cargo fmt`: rust code formatter

## Directories

- `~/.rustup`: rustup metadata and toolchains
- `~/.cargo`: cargo home directory
- `~/.cargo/bin`: rust commands directory

## Configuration

Add rust tools `bin` directory to shell path

    ~/.cargo/bin

## Help Docs

Open local rust docs

    rustup doc

## Rust Compiler

Compile rust file

    rustc <file>

Run compiled file

    ./<file>
    source <file>

## Rustup

Show current configured version and check for available updates

    rustup show
    rustup check

Update rust toolchains and rustup

    rustup update

## Cargo

Show cargo version

    cargo --version

Create new cargo project

    cargo new <project-name>

Add dependency (then install dependency via `cargo build`)

    cargo add <dependency>

Update cargo crate dependencies to latest semver minor release versions (major version bumps require editing `cargo.toml`)

    cargo update

Check package and dependencies for errors

    cargo check

Build project (`--release` or `-r` for release mode with build optimisations)

    cargo build
    cargo build --release

Execute generated binary to run debug or release build app

    ./target/debug/<app-binary>
    ./target/release/<app-binary>

Build and run project (in single step)

    cargo run

Run tests and benchmarking

    cargo test
    cargo bench

Document project (creates local docs for project and all dependencies)

    cargo doc
    cargo doc --open

Publish library to crates.io

    cargo publish

## VS Code

Extension: rust-analyzer

Format code: SHIFT + OPTION + F (can also be configured to format on save / paste)

## Clippy

Run clippy (rust linter) on project

    cargo clippy

Automatically fix linter issues that have known resolutions

    cargo fix
