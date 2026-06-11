# Generated TypeScript Baseline Diffs

This file records the migration baseline from the legacy Radroots TypeScript
generation path to the SDK-owned generation path.

## Current Baseline

The initial baseline was generated from `../radroots` with
`RADROOTS_TS_RS_EXPORT_DIR` pointed at `testdata/baseline/current-radroots-generated`.

Captured files:

- `testdata/baseline/current-radroots-generated/core/types.ts`
- `testdata/baseline/current-radroots-generated/events/constants.ts`
- `testdata/baseline/current-radroots-generated/events/kinds.ts`
- `testdata/baseline/current-radroots-generated/events/types.ts`
- `testdata/baseline/current-radroots-generated/identity/constants.ts`
- `testdata/baseline/current-radroots-generated/replica-db-schema/types.ts`
- `testdata/baseline/current-radroots-generated/trade/types.ts`
- `testdata/baseline/current-radroots-generated/types/types.ts`

The current legacy generation path did not produce a standalone
`events-indexed` TypeScript file from `typeshare` annotations. The SDK still
keeps `@radroots/events-indexed-bindings` in the approved package matrix because
the handoff requires that package and the upstream crate contains
generator-relevant type annotations.

`radroots_sql_wasm_core` still references `ts-rs` upstream, but no direct
generated output was discovered in the captured legacy package set. It remains
outside the Phase 1 SDK package matrix unless a later slice discovers a direct
generated output contract that contradicts this baseline.

## SDK Output Comparison

SDK-generated output now lives under `packages/*/src/generated`.

The approved package names remain root-import packages:

- `@radroots/core-bindings`
- `@radroots/events-bindings`
- `@radroots/events-indexed-bindings`
- `@radroots/identity-bindings`
- `@radroots/replica-db-schema-bindings`
- `@radroots/trade-bindings`
- `@radroots/types-bindings`

The SDK intentionally does not emit `@radroots/tangle-db-schema-bindings`.
The captured schema output is emitted from `@radroots/replica-db-schema-bindings`
instead.

Intentional differences from the legacy generated files:

- generated headers now identify `cargo xtask generate ts`;
- each package includes `src/generated/sdk-manifest.json`;
- `@radroots/events-bindings` emits the captured `types.ts`, `constants.ts`,
  and `kinds.ts` files and adds type-only imports from
  `@radroots/core-bindings` so strict package compilation succeeds;
- `@radroots/replica-db-schema-bindings` adds type-only imports from
  `@radroots/types-bindings` for `IResult`, `IResultList`, and `IResultPass`;
- `@radroots/trade-bindings` adds type-only imports from
  `@radroots/core-bindings` and `@radroots/events-bindings`, plus a local
  `bool` alias for the legacy generated spelling in the captured output;
- `@radroots/events-indexed-bindings` has SDK-authored TypeScript for the
  upstream wire structs because no committed legacy `typeshare` artifact was
  discoverable.

The SDK preserves the generated type and constant export names from the
captured baseline. It does not preserve old package-local handwritten helpers
such as runtime schemas or trade job-flow helper types that were not part of
the captured generated output.
