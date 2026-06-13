# AGENTS.md - Radroots SDK Repo Instructions

These instructions apply to the `rad-roots-labs/sdk` repository.

## Core Rules

- Work spec-first.
- Do not invent requirements.
- This repository owns the first-class Radroots SDK surfaces: the Rust `radroots_sdk` crate, generated TypeScript binding packages, and WebAssembly npm packages.
- Do not add UniFFI, Swift, Kotlin, Python, Go, or npm publishing in Phase 1.
- Do not add compatibility or legacy packages.
- Do not create `@radroots/tangle-db-schema-bindings`.
- Do not create `@radroots/contracts` in Phase 1.
- Do not modify downstream repos in this task.

## Expected Local Layout

```text
foundation/libs/rs/radroots
foundation/libs/rs/sdk
```

## Package Manager

Use `pnpm`.

## License

Use `MIT OR Apache-2.0`.

## Package Policy

All npm packages are private workspace packages in Phase 1.

Approved packages:

```text
@radroots/core-bindings
@radroots/events-bindings
@radroots/events-codec-wasm
@radroots/events-indexed-bindings
@radroots/identity-bindings
@radroots/replica-db-schema-bindings
@radroots/replica-db-wasm
@radroots/replica-sync-wasm
@radroots/trade-bindings
@radroots/types-bindings
```

Root imports only. No subpath exports in MVP.

## Generated Files

Commit:

```text
packages/*/src/generated/*.ts
packages/*/src/generated/sdk-manifest.json
```

Ignore:

```text
target/
dist/
node_modules/
artifacts/
```

All generated files must include generated-file headers and must be reproducible through:

```bash
cargo xtask generate ts
cargo xtask generate wasm
cargo xtask check
```

## Verification

Before committing, run the relevant subset of:

```bash
cargo fmt --all -- --check
cargo check --workspace
cargo test --workspace
cargo xtask check
cargo xtask generate wasm
pnpm -r build
pnpm -r typecheck
```

When modifying the upstream `radroots` repo, run its relevant Rust checks and search for leftover generator references.
