+++
id = "ADR-0139"
title = "ADR-0139: `compile-dot` target"
status = "open"
priority = "medium"
+++

---
title: '`compile-dot` target'
type: adr
date: 2026-10-16
status: accepted
status_note: Accepted — extracted in ADR-0128 Phase 7.
---

# ADR-0139: `compile-dot` target

## Context

[ADR-0114](../0114-handl-compile-plugin-architecture.md) states the compile
port (`Compiler` / `CompilerRegistry`). `plugin-ext-compile`'s dispatcher used
to register every compiler statically, so a DOT-only change rebuilt the whole
platform workspace.

## Decision

`dot` owns the Graphviz DOT compiler: `handl-plugin-compile-dot` (target
`dot`), which emits DOT over `Term` arrow graphs — here as
`modules/compile-dot`.

`host` keeps the port and the registry seam; a host opts the target in via
a feature on its own manifest (ADR-0128 §Registration).

## Consequences

- The `dot` target name is preserved (repo ≠ target).
- The sibling targets (`term`, `sexp`, `handl`, `js`, `llvm`) follow the same
  shape: `modules/compile-<target>` behind the same port.
- A DOT-specific change no longer rebuilds the platform workspace.
