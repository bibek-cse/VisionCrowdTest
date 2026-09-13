# Do Vision-Language Models Truly Count?

Official repository for **VisionCrowdTest**, a diagnostic benchmark for evaluating whether VLM crowd-count predictions are supported by spatial visual evidence.

## Overview

**VisionCrowdTest** investigates whether VLMs genuinely count individual instances in dense crowds or rely on coarse scene-level density cues.

<img width="2660" height="624" alt="Dataset (3)" src="https://github.com/user-attachments/assets/2c2db30e-10d4-4965-898d-c6a0445b3a72" />

The benchmark contains **1,304 images** and **398K+ annotated heads** across diverse datasets, modalities, viewpoints, and density regimes. Five VLMs are evaluated zero-shot for both **crowd counting** and **spatial grounding**.

Our analysis reveals a **Semantic-Localization Gap (SLG)**: VLMs can produce plausible crowd counts while showing weak spatial correspondence with the actual crowd distribution, particularly in highly congested scenes.

## Key Contributions

- **VisionCrowdTest:** 1,304 images with 398K+ annotated heads.
- **Multi-domain evaluation:** RGB, aerial, thermal, and infrared imagery.
- **Density-aware analysis:** Low, medium, and high-density crowds.
- **Zero-shot evaluation:** Five contemporary VLMs without fine-tuning.
- **Spatial attribution:** Prompt-conditioned Grad-CAM for visual grounding analysis.
- **Semantic-Localization Gap:** Measures the discrepancy between counting and spatial evidence.
- **Comprehensive metrics:** PMAE, CMAE, PMRE, CMRE, PMBE, CMBE, Attention-IoU, and GAME.

## Dataset

<img width="812" height="214" alt="Capture" src="https://github.com/user-attachments/assets/f43d2c12-9441-476e-b0f5-81f756b4800b" />

**Density regimes:**
- Low: y < 100
- Medium: 100 ≤ y < 500
- High: y ≥ 500

## Evaluated VLMs

<img width="2477" height="619" alt="Architecture (1)" src="https://github.com/user-attachments/assets/66104041-40cf-4a24-8392-7e91873ddc70" />

- InternVL3.5-8B
- Ovis2.5-9B
- Qwen3-VL-8B
- Gemma-3-12B
- Ministral-3-8B

## Metrics

- **PMAE:** Semantic counting error.
- **CMAE:** Grad-CAM-supported counting error.
- **Attention-IoU:** Spatial overlap between attribution and ground truth.
- **GAME:** Spatial distribution consistency.
- **SLG:** Difference between semantic and localization-supported counting.

