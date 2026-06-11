# Radroots SDK

TypeScript bindings workspace for Radroots Rust contracts.

## Scope

This repository owns generated TypeScript binding packages for the Radroots Rust
crate family. Phase 1 is limited to private pnpm workspace packages generated
from Rust binding crates.

## Packages

The approved TypeScript package set is:

- `@radroots/core-bindings`
- `@radroots/events-bindings`
- `@radroots/events-indexed-bindings`
- `@radroots/identity-bindings`
- `@radroots/replica-db-schema-bindings`
- `@radroots/trade-bindings`
- `@radroots/types-bindings`

The legacy `@radroots/tangle-db-schema-bindings` package is intentionally not
part of this SDK.

## Generation

Generated TypeScript source is committed under `packages/*/src/generated`.

```bash
cargo xtask generate ts
cargo xtask check
pnpm -r build
pnpm -r typecheck
```

## License

Licensed under either of:

- Apache License, Version 2.0
- MIT License
