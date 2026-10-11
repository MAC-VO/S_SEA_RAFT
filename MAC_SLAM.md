# MAC-SLAM integration

This fork starts at upstream commit `9137517ba24e628442aec097d3afe71d03503b75`.
The network is importable as a package; standalone commands still run from this repository root.

`RAFT(args, init_weights=False)` constructs the same architecture without downloading
ImageNet initialization when a complete checkpoint will immediately be loaded.

`forward(..., test_mode=True, return_features=True)` additionally returns `initial`
and `contexts`. Each context concatenates the static context, current motion feature,
and refined hidden state in that order. The default call retains the upstream outputs.
`encoder_amp=True` runs only the context/feature encoders under BF16 autocast.

MAC-SLAM owns covariance heads, training, checkpoints, and frontend adapters outside this
submodule. The upstream license and attribution remain in LICENSE and README.md.
