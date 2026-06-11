# Consumer Migration

The SDK preserves the approved generated binding package names used by Radroots
TypeScript consumers:

- `@radroots/core-bindings`
- `@radroots/events-bindings`
- `@radroots/events-indexed-bindings`
- `@radroots/identity-bindings`
- `@radroots/replica-db-schema-bindings`
- `@radroots/trade-bindings`
- `@radroots/types-bindings`

Consumers should keep root imports from those packages. Subpath exports are not
part of this phase.

The schema package was renamed during extraction. Consumers of the retired
`@radroots/tangle-db-schema-bindings` package should migrate imports to
`@radroots/replica-db-schema-bindings`. The SDK does not provide a compatibility
alias or re-export package for the retired name.

The SDK packages contain generated types, generated constants, and generated
manifest files. Deprecated handwritten helpers from old package directories,
including runtime schemas and trade job-flow helper types, are not generated
binding outputs in this phase.
