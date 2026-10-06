# PtychoPINN object bank, object law v4

1,200 complex objects (392 × 392, complex64) used to simulate ptychography training data in
[PtychoPINN](https://github.com/hoidn/PtychoPINN): 1,000 training, 100 validation, 100 test.
Each object is derived from one 392-px crop of an ImageNet 2012 training image under object law v4
(red channel → amplitude, green channel → phase, through a per-object material, photon-energy and
thickness draw; `docs/studies/object_law_v4.md` in PtychoPINN). The manifest records every object's
source image, crop, law parameters and the sha256 of its array.

| Asset | Content |
|---|---|
| `object_bank_manifest.json` | Law id, split sizes, per-object provenance and hashes |
| `frozen_train_validation.npz` | `trainObjectGuess` (1000, 392, 392), `testObjectGuess` (100, 392, 392): training and validation objects |
| `test_objects.npz` | `object_ids` (100,), `objectGuess` (100, 392, 392): test objects |

Checksums: `SHA256SUMS`. PtychoPINN's `scripts/studies/probe_matched_pipeline.py train` downloads
and verifies these files itself; by hand:
`gh release download v4-bank-1 -R hoidn/ptychopinn-object-law-v4 -D objects/`.

## Terms

The objects are derived from ImageNet and inherit the
[ImageNet terms of access](https://image-net.org/download): non-commercial research and educational
use only; no further redistribution; cite Russakovsky et al., *ImageNet Large Scale Visual
Recognition Challenge*, IJCV 2015. The source images and the RGB crops are not included.
