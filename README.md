# Radroots SDK

Developer-facing SDK workspace for Radroots Rust contracts.

## Scope

This repository owns the first-class Rust `radroots_sdk` crate, generated
TypeScript binding packages, and WebAssembly npm package surfaces for the
Radroots Rust crate family.

## Packages

The approved TypeScript package set is:

- `@radroots/core-bindings`
- `@radroots/events-bindings`
- `@radroots/events-codec-wasm`
- `@radroots/events-indexed-bindings`
- `@radroots/identity-bindings`
- `@radroots/replica-db-schema-bindings`
- `@radroots/replica-db-wasm`
- `@radroots/replica-sync-wasm`
- `@radroots/trade-bindings`
- `@radroots/types-bindings`

The legacy `@radroots/tangle-db-schema-bindings` package is intentionally not
part of this SDK.

## Generation

Generated TypeScript source is committed under `packages/*/src/generated`.

```bash
cargo xtask generate ts
cargo xtask generate wasm
cargo xtask check
pnpm -r build
pnpm -r typecheck
```

## License

Licensed under either of:

- Apache License, Version 2.0
- MIT License
