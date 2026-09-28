# Provenance: laya-multilingual (f4064eb56fb7f7d325e1)

The laya-multilingual profile distributes no OpenKind-generated assets: every artifact
its manifest pins is fetched directly from the checkpoint author's Hugging
Face repository, which stays the canonical source.

- Hugging Face repository: `convaiinnovations/laya-multilingual`
- Pinned revision: `e4e9ddf21a7b1903b7acffd8814ad4307bf63a67`
- Profile ID: `f4064eb56fb7f7d325e1`
- OpenKind manifest SHA-256: `226fc3d993fbc2f1b7d24ae553832180467c27b532f94cba519a0ed380e0e0e4`
- Upstream license: Apache-2.0 (see `LICENSE-LAYA` at the mirror root);
  the multilingual encoder additionally derives from `jhu-clsp/mmBERT-base`
  (MIT).

Weights are deliberately not mirrored: shards remain at their authors'
repository and are digest-verified in place after download. The reference
Python implementation (github.com/NandhaKishorM/laya, Apache-2.0) is also
not redistributed here.
