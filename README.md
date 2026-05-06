# Real-Time Video Streams with Flexible Sliding Mechanism

This repository provides the source code and configuration files for the paper:

**Edge Environment-Oriented Action Recognition Framework for Real-Time Video Streams with a Flexible Sliding Mechanism**

## Paper Reproduction

The core reproduction code includes:

- C3D-based clip-level action recognition baseline
- Frame-by-frame sliding baseline
- Flexible sliding mechanism
- GMM-based background-window skipping
- Inter-frame-difference-based vague-window skipping
- Streaming evaluation scripts
- Threshold sensitivity and robustness analysis scripts

## Additional Experimental Modules

This repository also includes optional experimental extensions, such as LiteVT, MATClip, token cache, and uncertainty-aware thresholding. These modules are provided for further exploration and are not the main contribution evaluated in the manuscript.

The project keeps the paper's scheduling skeleton unchanged:

- `16-frame` clip input
- `K + 2` classifier head (`K` actions + `Background` + `Vague`)
- `frame-by-frame` sliding when the current window is a target action
- `GMM + Pearson correlation` for background-window skipping
- `inter-frame difference` for vague-window skipping
- streaming evaluation with `FPS`, `Speed Ratio`, delay, average sliding step, skip ratio, and cache hit rate

## Experiment Matrix

Use these seven settings to separate paper contribution from your own:

- `B0`: `C3D + FrameByFrame`
- `B1`: `C3D + FlexibleSliding`
- `B2`: `LiteVT + FrameByFrame`
- `B3`: `LiteVT + FlexibleSliding`
- `B4`: `LiteVT + FlexibleSliding + TokenCache`
- `B5`: `LiteVT + FlexibleSliding + UncertaintyThreshold`
- `B6`: `LiteVT + FlexibleSliding + TokenCache + UncertaintyThreshold`

## Project Layout

```text
configs/                 YAML experiment presets
scripts/                 train / offline eval / streaming eval entrypoints
src/edgeflex/data/       clip sampling and labels
src/edgeflex/models/     C3D baseline and LiteVT backbone
src/edgeflex/scheduler/  flexible sli
