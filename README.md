<div align="center">

# HMR-1: Hierarchical Massage Robot with Vision-Language-Model for Embodied Healthcare

[![License](https://img.shields.io/badge/License-MIT-green.svg)]()
[![Last Commit](https://img.shields.io/badge/last%20commit-March%202026-yellowgreen)]()
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-orange)]()


</div>

# Introduction

This repository presents **HMR-1**, a hierarchical massage robot framework for embodied healthcare.  
HMR-1 integrates a **high-level acupoint grounding module** powered by vision-language models and a **low-level control module** for trajectory planning and robotic execution. To support this task, we construct **MedMassage-12K**, a multimodal dataset containing large-scale acupoint images and QA pairs under diverse lighting and background conditions.  
Our framework enables robots to understand natural language instructions, localize target acupoints, and perform precise massage actions in real-world environments.

![Alt Text](illustrates.png)
---

# Dataset

**MedMassage-12K** is a multimodal dataset for embodied massage and acupoint grounding.  
It includes large-scale image-text samples collected under diverse lighting, background, and pose conditions, and is designed to support language-guided acupoint localization, multimodal reasoning, and robotic massage execution in real-world healthcare scenarios.

![Alt Text](dataset
.png)

## 1. Dataset Preparation

### Download Dataset
#### (1) DUO dataset (https://github.com/chongweiliu/DUO)
#### (2) RUOD dataset (https://github.com/dlut-dimt/RUOD))

### Dataset Structure

Please download and organize the datasets with the following structure:

```text
datasets/
├── DUO/
│   ├── images/
│   │   ├── train/
│   │   └── val/
│   ├── labels/
│   │   ├── train/
│   │   └── val/
│   └── DUO.yaml
│
└── RUOD/
    ├── images/
    │   ├── train/
    │   └── val/
    ├── labels/
    │   ├── train/
    │   └── val/
    └── RUOD.yaml
```

### Configuration File

Use `datasets/data_RUOD.yaml` to configure the dataset path. An example is shown below:

```yaml
path: ./datasets/RUOD   # dataset root directory
train: images/train
val: images/val
nc: 10                                   # number of classes
names: ['holothurian', 'boat', 'echinus', 'starfish', 'fish', 'corals', 'diver', 'cuttlefish', 'turtle', 'jellyfish']
```

## 2、Pretrained Weights

You can download the pretrained weight file **`rtdetr-r50.pt`** from Baidu Netdisk:

- **Link**: [https://pan.baidu.com/s/1-yge3B-41eaUIiQOyxs0FQ](https://pan.baidu.com/s/1-yge3B-41eaUIiQOyxs0FQ)
- **Extraction Code**: `PKGR`
- 
After downloading, please place the weight file in the appropriate directory before training or evaluation.

## 3. Model Training

```bash
# Basic training command (using default configuration)
python3 ./train.py
```
## 4. Model Validation

```bash
# Basic training command (using default configuration)
python3 ./val.py
```


