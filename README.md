mrly-core; a MrlyMath crate: the substrate, tensors, cells, colors, images, resampling, seeded chance and the canonical names

# CORE

- One repo, one crate, one version; `js/`, `py/` and `cli/` are its bindings, written by `mrly-bridge`: `@mrlyprod/core` (npm), `mrly.core` (PyPI `mrly-core`) and the `mrly-core` command.
- The hand-written crossings live in `src/hand/` behind the cargo features `js`, `py` and `cli`; a leaf of another unit takes `mrly-core = { version, features = ["js"] }`.
- `scripts/bridge.sh` regenerates the leaves from `bridge.toml` and the sources; `scripts/bridge.sh check` says what is stale.
- `scripts/check.sh` is the one gate: fmt, clippy, test, doc, bridge check, ruff, wasm, the leaves' tests, leak.
- A fresh clone runs `scripts/wasm.sh` once before any host builds: it writes `js/pkg/`, which is not committed.
- Until the crates are published, clone the fleet beside this repo: `scripts/bridge.sh` runs the sibling `../bridge`, and a `.cargo/config.toml` with `[patch.crates-io]` rows points every `mrly-*` dependency at its sibling folder.
- Every file `.gitattributes` marks `linguist-generated` is the bridge's; never hand-edit one.
- Docs: [docs.rs/mrly-core](https://docs.rs/mrly-core).
