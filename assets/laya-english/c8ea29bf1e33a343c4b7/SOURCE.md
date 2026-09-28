# Provenance: laya-english (c8ea29bf1e33a343c4b7)

The laya-english profile distributes no OpenKind-generated assets: every artifact
its manifest pins is fetched directly from the checkpoint author's Hugging
Face repository, which stays the canonical source.

- Hugging Face repository: `convaiinnovations/laya`
- Pinned revision: `55cf4c4ebb4ebe31b2550e8bdf3bd21b99753851`
- Profile ID: `c8ea29bf1e33a343c4b7`
- OpenKind manifest SHA-256: `eb6bb23fb3a1b7d5d7f0a647d68f455cc7b5b01bac532078dc2da8aba31f76f2`
- Upstream license: Apache-2.0 (see `LICENSE-LAYA` at the mirror root);
  the multilingual encoder additionally derives from `answerdotai/ModernBERT-large`
  (Apache-2.0).

Weights are deliberately not mirrored: shards remain at their authors'
repository and are digest-verified in place after download. The reference
Python implementation (github.com/NandhaKishorM/laya, Apache-2.0) is also
not redistributed here.
