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

SDK-generated output has not been produced yet. Later generation slices must
update this file with intentional differences between the baseline above and
`packages/*/src/generated`.
