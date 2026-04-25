# AI-Based Estimation of Air Pollution in Bishkek, Kyrgyzstan Using Urban Images

## Overview
This repository contains the code and dataset description for the paper:
**"AI-Based Estimation of Air Pollution in Bishkek, Kyrgyzstan Using Urban Images"**
submitted to Preprints.org (MDPI).

**Authors:** Mokhammad Parvani Vafa, Mohd Tauheed Khan  
**Affiliation:** Department of Computer Science, Ala-Too International University (AIU), Bishkek, Kyrgyzstan

---

## Abstract
This study investigates the feasibility of estimating air pollution 
from urban photographs using deep learning and transfer learning techniques. 
Two pre-trained CNN architectures, VGG16 and EfficientNetB0, were evaluated 
in hybrid multimodal regression models combining image features with PM2.5 
sensor data. A locally collected dataset of 1,014 image–AQI pairs was used. 
EfficientNetB0 outperformed VGG16 across all metrics (RMSE: 66.49 vs 78.71, 
MAE: 49.00 vs 58.78, R²: −0.28 vs −0.79).

---

## Dataset
- **Total samples:** 1,014 image–AQI pairs
- **Split:** 710 train / 151 validation / 153 test
- **Images:** Urban photographs taken in Bishkek, Kyrgyzstan
- **Labels:** AQI values from nearest monitoring station at time of capture
- **Note:** Raw images are not publicly shared due to privacy considerations.
  Dataset available upon reasonable request.

---

## Models

### VGG16 Hybrid
- Backbone: VGG16 pretrained on ImageNet
- Input: 224×224 image + PM2.5 scalar
- Head: GAP → 512-dim → concat PM2.5 → Dense(128, ReLU) → Linear output

### EfficientNetB0 Hybrid
- Backbone: EfficientNetB0 pretrained on ImageNet
- Input: 224×224 image + PM2.5 scalar
- Head: GAP → 1280-dim → concat PM2.5 → Dense(128, ReLU) → Linear output

---

## Results

EfficientNetB0 reduces RMSE by **15.5%** and MAE by **16.6%** compared to VGG16.

---

## Requirements
tensorflow>=2.10
numpy
pandas
matplotlib
scikit-learn
pillow

Install with:
```bash
pip install -r requirements.txt
```

---

## Training
Training was conducted in Google Colaboratory on an NVIDIA T4 GPU.  
Open `notebooks/training.ipynb` in Google Colab to reproduce results.

**Two-phase training:**
- Phase 1: Frozen backbone, head only, lr=1e-4, 15 epochs
- Phase 2: Top-4 layers unfrozen, lr=1e-5, 8 epochs

---

## Citation
If you use this work, please cite:
@article{parvanivafa2026aqi,
title={AI-Based Estimation of Air Pollution in Bishkek,
Kyrgyzstan Using Urban Images},
author={Parvani Vafa, Mokhammad and Khan, Mohd Tauheed},
year={2026},
institution={Ala-Too International University}
}

---

## Contact
**Email:** porvanivafoo@gmail.com  
**Institution:** Ala-Too International University, Bishkek, Kyrgyzstan
