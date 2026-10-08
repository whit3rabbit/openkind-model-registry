# OpenKind model registry

This public repository distributes curated profiles for the OpenKind decision
engine. The private OpenKind application repository owns the catalog metadata,
compiled-in loaders, CLI, and daemon. Its `registry/v1` is mirrored here so
`openkind catalog` and `openkind pull` can use anonymous raw HTTPS requests.
The supplemental MLX alternatives index is for discovery only. It does not add
entries to `openkind catalog` or make Hugging Face conversions pullable.
[`registry/v1/jev-gev-mlx-models.json`](registry/v1/jev-gev-mlx-models.json)
pins two JEV-protocol 8-bit MLX conversions (JEV-27B-VL and GEV-26B-Decide)
the same way: research metadata only, not installable.

| Here | OpenKind application repository | Model authors |
|---|---|---|
| Public `registry/v1` mirror, small profile bundle, exported tokenizer | Metadata source, loader code, `scripts/sync-model-registry.py` | Checkpoint weights |

The first entry is the pinned Qwen3.5-4B state-first integration target. Its
`rust-loadable` status does not claim task quality or release approval.
Checkpoint shards remain at `Qwen/Qwen3.5-4B-Base`, pinned to commit
`1001bb4d826a52d1f399e183466143f4da7b741b`; clients verify their size and
SHA-256. The Qwen license is in [`LICENSE-QWEN`](LICENSE-QWEN). The
[bundle source note](assets/qwen35-state-first/a047d6802c3f06f085b8/bundle/SOURCE.md)
records profile provenance.

## Jeeves is not a catalog entry

Jeeves is an external comparator, not an OpenKind catalog profile. There is no
Jeeves manifest or compiled-in Rust loader here, so `openkind pull jeeves` and
`openkind serve --installed-models jeeves` are unsupported. Its weights remain
at the model author's repository and its separate reference runtime is outside
this registry.

## Publishing a catalog change

Commit new profile assets here first. Keep their commit reachable, then pin
that commit and each artifact digest in OpenKind's manifest. Update OpenKind's
catalog manifest digest and pass its local loader and parity checks. From the
OpenKind checkout, run:

```bash
python3 scripts/sync-model-registry.py --write
# Review, commit, and push registry/v1 in this repository.
python3 scripts/sync-model-registry.py --remote
```

The script is in OpenKind, not this repository. `--write` copies all metadata
under `registry/v1`, including supplemental indexes; it does not copy profile
assets, commit, or push. `--remote` checks the public metadata and pinned
profile assets after the push. Both commands leave checkpoint shards with their
authors. There is no automatic cross-repository push. The script defaults to
`~/Documents/GitHub/openkind-model-registry`; pass `--mirror PATH` if this
checkout is elsewhere.
