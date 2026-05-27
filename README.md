# VisionCrowdTest

> **Do Vision-Language Models Truly Count? A Zero-Shot Study of Spatial Enumeration in Dense Crowd Scenes**

VisionCrowdTest is a unified benchmark and evaluation framework designed to systematically analyze the **spatial counting**, **localization consistency**, and **density-aware reasoning** capabilities of modern Vision-Language Models (VLMs) in dense crowd scenes. The benchmark evaluates whether large multimodal models preserve fine-grained spatial understanding under highly congested visual conditions or increasingly rely on coarse crowd-level representations.

This repository accompanies the paper:

> **Do Vision-Language Models Truly Count? A Zero-Shot Study of Spatial Enumeration in Dense Crowd Scenes** 

---

## 🚀 Highlights


* Unified **zero-shot crowd counting benchmark** for modern VLMs
* Multi-domain evaluation:

  * RGB crowd scenes
  * Aerial imagery
  * Thermal imagery
  * Infrared crowd scenes
  * Surveillance environments
* Density-aware evaluation:

  * Low-density
  * Medium-density
  * High-density crowds
* Spatial grounding analysis using:

  * Grad-CAM localization
  * Attention-IoU
  * GAME metrics
* Benchmark supports multiple VLMs:

  * Qwen3-VL
  * InternVL3.5
  * Ovis2.5
  * Gemma-3
  * Ministral-3

---

# 📌 Motivation

Modern Vision-Language Models demonstrate impressive multimodal reasoning abilities, but their capability for **fine-grained spatial counting** in dense visual scenes remains largely unexplored.

Dense crowd counting requires:

* Localized spatial reasoning
* Instance-aware representation
* Occlusion robustness
* Scale-aware perception
* Fine-grained enumeration

VisionCrowdTest investigates whether current VLM architectures can preserve reliable spatial grounding under severe crowd congestion.

---

# 🧠 Framework Overview

The proposed framework performs:

1. Visual tokenization
2. Prompt-guided multimodal reasoning
3. Autoregressive crowd count prediction
4. Grad-CAM-based localization analysis
5. Density-aware spatial consistency evaluation

The framework evaluates both:

* **Semantic counting accuracy**
* **Spatial grounding fidelity**

---

## 📂 Benchmark Datasets

VisionCrowdTest integrates multiple challenging crowd-counting datasets spanning diverse visual domains, sensing modalities, viewpoints, and density regimes.

| Dataset | Img | Max Resolution | Min Resolution | Mean Resolution | Avg. Resolution | Max Count | Min Count | Avg. Count | Total Count |
|---|---|---|---|---|---|---|---|---|---|
| JHU-Crowd++ | 319 | (7164,4630) | (250,250) | (1345.2,873.8) | (1920,1080) | 6210 | 1 | 278.59 | 88,870 |
| DLR-ACD | 14 | (5616,3744) | (1545,2350) | (5109.2,3500.4) | (5184,3456) | 19,286 | 285 | 6295.71 | 88,140 |
| UCF-QNRF | 100 | (5969,3979) | (600,400) | (2958.4,2028.1) | (3456,2304) | 4535 | 117 | 757.37 | 75,737 |
| UCF50 | 50 | (1024,1024) | (496,328) | (902.6,653.8) | (984,648) | 4633 | 96 | 1279.48 | 63,974 |
| ShanghaiTech Part-A | 100 | (992,1024) | (300,200) | (866.8,577.7) | (1024,511) | 1266 | 66 | 402.30 | 40,230 |
| ShanghaiTech Part-B | 100 | (1024,768) | (1024,768) | (1024.0,768.0) | (1024,768) | 539 | 15 | 122.26 | 12,226 |
| RGBT-CC | 161 | (640,480) | (640,480) | (640.0,480.0) | (640,480) | 348 | 12 | 70.61 | 11,368 |
| DroneRGBT | 360 | (640,512) | (640,512) | (640.0,512.0) | (640,512) | 175 | 1 | 27.90 | 10,044 |
| CityStreet | 100 | (2704,1520) | (2704,1520) | (2704.0,1520.0) | (2704,1520) | 123 | 35 | 76.19 | 7,619 |

The benchmark contains:

- **1304 test images**
- **398K+ annotated head instances**
- Multi-domain crowd scenes
- RGB, Thermal, and Infrared modalities
- Crowd populations exceeding **19,000 people per image**
- Low, medium, and high-density crowd regimes

---

# 📊 Evaluation Metrics

## Semantic Counting Metrics

* MAE
* MSE
* RMSE
* MRE
* MBE

## Spatial Grounding Metrics

* Attention-IoU
* GAME(L)
* Grad-CAM-based localization count

---

# 🏗️ Repository Structure

```bash
VisionCrowdTest/
│
├── datasets/
│   ├── JHU/
│   ├── DLR_ACD/
│   ├── QNRF/
│   ├── UCF50/
│   ├── ShanghaiTech/
│   ├── RGBT_CC/
│   ├── DroneRGBT/
│   └── CityStreet/
│
├── models/
│   ├── qwen/
│   ├── internvl/
│   ├── ovis/
│   ├── gemma/
│   └── mistral/
│
├── evaluation/
│   ├── metrics.py
│   ├── localization.py
│   ├── attention_iou.py
│   └── game_metric.py
│
├── visualization/
│   ├── gradcam.py
│   ├── overlay.py
│   └── qualitative_analysis.py
│
├── scripts/
│   ├── evaluate.py
│   ├── inference.py
│   └── patchify.py
│
├── results/
│
├── figures/
│
├── requirements.txt
│
└── README.md
```

---

# ⚙️ Installation

## Clone Repository

```bash
git clone https://github.com/bibek-cse/VisionCrowdTest.git
cd VisionCrowdTest
```

## Create Environment

```bash
conda create -n visioncrowd python=3.10
conda activate visioncrowd
```

## Install Dependencies

```bash
pip install -r requirements.txt
```

---

# 🖥️ Supported Models

| Model | Type | Hugging Face |
|---|---|---|
| Qwen3-VL | Vision-Language Model | [Qwen/Qwen3-VL-8B-Instruct](https://huggingface.co/Qwen/Qwen3-VL-8B-Instruct) |
| InternVL3.5 | Multimodal Transformer | [OpenGVLab/InternVL3_5-8B](https://huggingface.co/OpenGVLab/InternVL3_5-8B) |
| Ovis2.5 | Large VLM | [AIDC-AI/Ovis2.5-9B](https://huggingface.co/AIDC-AI/Ovis2.5-9B) |
| Gemma-3 | Open Multimodal LLM | [google/gemma-3-12b-it](https://huggingface.co/google/gemma-3-12b-it) |
| Ministral-3 | Vision-Language Model | [mistralai/Ministral-3-8B-Instruct-2512-BF16](https://huggingface.co/mistralai/Ministral-3-8B-Instruct-2512-BF16) |

---

# 📈 Example Evaluation

## Run Zero-Shot Evaluation

```bash
python scripts/evaluate.py \
    --model qwen3_vl \
    --dataset QNRF \
    --patch_size 512
```

---

# 🔥 Grad-CAM Visualization

```bash
python visualization/gradcam.py \
    --model gemma3 \
    --image sample.jpg
```

This generates:

* Attention heatmaps
* Spatial grounding overlays
* Localization consistency maps

---

# 🧩 Patchification Strategy

For extremely dense scenes, VisionCrowdTest supports localized patch-based inference:

```bash
python scripts/patchify.py \
    --patch_size 512
```

Patchification helps:

* Preserve local spatial fidelity
* Reduce token saturation
* Improve dense-scene stability

---

# 📌 Key Findings

Our experiments reveal:

* Progressive degradation in spatial consistency with increasing crowd density
* Persistent undercounting in highly congested scenes
* Weak localization fidelity despite semantically plausible predictions
* Heavy reliance on coarse crowd-level representations
* Significant semantic-localization discrepancy across modern VLMs

---

# 📷 Qualitative Analysis

The framework provides:

* Grad-CAM visualizations
* Attention-region overlays
* Density-aware localization analysis
* Semantic vs localization discrepancy analysis

---

# 🤝 Acknowledgement

Special thanks to:

* Aryabhatta Supercomputing Centre (ASC), IIT Patna
* All publicly available crowd-counting benchmark providers
  
---
