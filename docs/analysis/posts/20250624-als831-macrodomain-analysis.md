---
date: 
  created: 2025-06-29
  updated: 2025-08-08
tags:
    - ALS 8.3.1
    - Macrodomain
    - mdx2
authors:
    - spmeisburger
---

# Preliminary results: macrodomain diffuse scattering at ALS 8.3.1 on June 24, 2025

We collected diffraction data from several SARS-CoV-2 NSP3 macrodomain crystals at room temperature, and created preliminary diffuse maps for 3 crystals using mdx2. Interestingly, the diffuse maps appear quite different. The reason for this is not apparent yet.

<!-- more -->

I think more measurements should definitely be done if possible, and with greater care. However, the existing data are valuable as examples of how diffuse scattering might be influenced by beam properties, crystal handling, data processing algorithms, etc.

## Data collection

[2025-06-24 @ ALS 8.3.1](../../beamtime/20250624-als.md)

## Bragg data results

- processed using xia2 (DIALS pipeline) 
- cut the number of frames according to merging statistics (consistent Rmerge, B-factor increase < 2 Å^2, etc).
    - `H6_5` (high dose rate): kept 900 frames (90 degrees)
    - `H8_8` (medium dose rate): kept 3600 frames (360 degrees), but noted rise in R-merge beyond frame ~3000
    - `G8_1` (low dose rate): kept 3600 frames (360 degrees)
- All 3 datasets processed to 1.08 Å (CC1/2 > 0.33), and have good statistics.
- The unit cell dimensions are different by up to ~0.2 Å, perhaps from exposure to dry air during harvesting?

## Diffuse maps

Processed using mdx2, integrating on a 2x2x4 (coarse) grid. Rendered slices in a non-halo plane (l=1/2), intensity scale is arbitrary (normalized to 1).

| `H6_5` (high dose rate) |
| --- |
| ![mac_H6_slice_lp5.png](7b1a4bfb-7d80-4814-8746-c83f866c0985.png) |

| `H8_8` (medium dose rate) |
| --- |
| ![mac_H8_slice_lp5.png](accc6ec6-9939-4540-b0d2-c51b1e2f52e8.png) |

| `G8_1` (low dose rate) |
| --- |
| ![mac_G8_slice_lp5.png](31b14724-0609-4b8b-b436-dea7c2cd99e6.png) |

## Observations

- The isotropic component is quite different between `H6_5` (high dose rate) and `H8_8` (medium dose rate).
- The diffuse fluctuations are strongest for `H8_8` (medium dose rate)
- The signal-to-noise appears to be best for `H6_5` (high dose rate), however the features are perhaps more washed out?
- The maps are very noisy for `G8_1` (low dose rate), but pattern of fluctuations appears distinct from the others

## Questions

1. How different are the structures / B-factors for these crystals? (try structure refinement?)
2. What was the absorbed dose for each dataset? (talk to James H)
3. Do we expect the crystals to be isomorphous? were the well solutions the same? (talk to James F)

## Next steps

1. Characterize (experimentally)
    1. Repeatability (use humid environment for harvesting)
    2. Radiation damage effects
    3. Artifacts from low signal-to-noise (use larger crystals? multi-crystal merging?)
2. Investigate (via data processing, analysis)
    1. What do the halos look like?
    2. Is the isotropic component time-dependent?
    3. Do the Bragg and diffuse scale factors agree?
    4. In general, do scaling & merging algorithms in mdx2 behave optimally when signal-to-noise is low?
