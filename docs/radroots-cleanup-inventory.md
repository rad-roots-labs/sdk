# Radroots Cleanup Inventory

After SDK parity is proven, the Radroots repository can drop TypeScript
generator concerns from these crates:

- `core`
- `events`
- `events_indexed`
- `identity`
- `replica_db_schema`
- `sql_wasm_core`
- `trade`
- `types`

Cleanup scope:

- remove `ts-rs` and `typeshare` dependencies and workspace pins;
- remove generator features and feature forwarding;
- remove generator build scripts and export-directory tests;
- remove `TS` derives, `typeshare` annotations, and generated-output-only field
  attributes;
- keep serde, Rust domain behavior, runtime tests, and public Rust APIs intact.

The SDK baseline did not discover committed generated TypeScript output for
`sql_wasm_core` or legacy `events_indexed` `typeshare` output. `events_indexed`
is generated in the SDK from the current upstream wire structs because the
handoff requires `@radroots/events-indexed-bindings`.
