# OpenKind model registry

This public repository distributes curated profiles for the OpenKind decision
engine. The private OpenKind application repository owns the catalog metadata,
compiled-in loaders, CLI, and daemon. Its `registry/v1` is mirrored here so
`openkind catalog` and `openkind pull` can use anonymous raw HTTPS requests.

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

## Jeeves native MLX profile

`jeeves:15fb3b95801f2f039636` pins the 4-bit
[cowWhySo/jeeves-mlx export](https://huggingface.co/cowWhySo/jeeves-mlx/tree/6f4220a267a94c5279b3fcbc5499de734b9a55b0).
Its approximately 5.07 GB of artifacts stay on Hugging Face. The manifest
includes the FP32 pointer head, tokenizer, configuration, and license files.

Serving requires an OpenKind build containing the Jeeves loader, with
`--features mlx` on macOS arm64. The profile scores an empty reasoning chain
and returns typed Noul, Choice, and Score answers. It is a Rust-loadable
prototype; task quality and release promotion remain separate gates.

```bash
openkind pull jeeves:15fb3b95801f2f039636
openkind serve --installed-models jeeves:15fb3b95801f2f039636
```

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

The script is in OpenKind, not this repository. `--write` copies only catalog
and manifest files; it does not copy assets, commit, or push. `--remote` checks
the public catalog, manifests, and pinned profile assets after the push. Both
commands leave checkpoint shards with their authors. There is no automatic
cross-repository push. The script defaults to a checkout at
`~/Documents/GitHub/openkind-model-registry`; pass `--mirror PATH` if this
checkout is elsewhere.
