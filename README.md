# OpenKind model registry staging

This repository is staged locally for review. It contains the pinned OpenKind state-first profile bundle and tokenizer needed by the native Rust loader. Base Qwen3.5 weights are not copied here; clients download them from the Qwen repository at its pinned revision and verify SHA-256. The profile is Rust-loadable, not task-qualified or release-promoted. Publication requires explicit approval because these files currently come from a private repository.
