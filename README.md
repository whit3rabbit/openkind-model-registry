# OpenKind model registry

This static catalog describes curated OpenKind model profiles. The first profile is the pinned Qwen3.5-4B state-first integration target. It is Rust-loadable but has no task-quality or release-promotion claim.

The registry contains the small OpenKind profile bundle and the exported tokenizer required by its loader. It does not rehost the Qwen checkpoint shards. Clients download those shards from `Qwen/Qwen3.5-4B-Base` at commit `1001bb4d826a52d1f399e183466143f4da7b741b` and verify size and SHA-256. Qwen model licensing is reproduced in `LICENSE-QWEN`; see `assets/qwen35-state-first/a047d6802c3f06f085b8/bundle/SOURCE.md` for profile provenance.

`registry/v1/catalog.json` is the entry point. Each named manifest pins its artifacts to immutable source commits.
