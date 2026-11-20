# engine-compile-dot

Graphviz DOT compiler for `Term` arrow graphs — part of the `engine-compile-*`
compiler-backend family: consumes Handl `Term` arrow terms and emits
Graphviz DOT source for visualization.

The crate lives in `modules/compile-dot` inside this workspace.

## Development

```bash
cargo xtask gate        # fmt --check → clippy -D warnings → test → doc
```

`cargo xtask` wraps the repo's `xtask/` crate (`fmt`, `clippy`, `test`, `doc`,
`check`, `gate`); `ci.sh` is the gate entry. Deps resolve from git, so no
sibling checkouts are needed; a plain clone test-runs as-is.

## License

MIT.
