# Provenance: laya-typed-decisions (9d28cfa9567902801ed1)

The laya-typed-decisions profile distributes no OpenKind-generated assets: every artifact
its manifest pins is fetched directly from the checkpoint author's Hugging
Face repository, which stays the canonical source.

- Hugging Face repository: `convaiinnovations/laya-typed-decisions`
- Pinned revision: `1a793eb568e6718f15941d08f85432581df534e3`
- Profile ID: `9d28cfa9567902801ed1`
- OpenKind manifest SHA-256: `84ddbbcfe1ba6909008bf6c1f8115c73bd2e147b5acf01a1a82d76b04d955417`
- Upstream license: Apache-2.0 (see `LICENSE-LAYA` at the mirror root);
  the multilingual encoder additionally derives from `answerdotai/ModernBERT-large`
  (Apache-2.0).

Weights are deliberately not mirrored: shards remain at their authors'
repository and are digest-verified in place after download. The reference
Python implementation (github.com/NandhaKishorM/laya, Apache-2.0) is also
not redistributed here.
