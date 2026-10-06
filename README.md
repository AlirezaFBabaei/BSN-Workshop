# BSN Workshop: Lung Sound Classification with Frozen Deep Learning Models

Hands-on notebook for the IEEE BSN 2026 workshop. Attendees explore ICBHI 2017 lung-sound recordings,
try different preprocessing settings, train a small classification head on precomputed embeddings from
six pretrained models, and export the head as ONNX.

## Run it

**Google Colab (recommended, nothing to install):**
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AlirezaFBabaei/BSN-Workshop/blob/main/BSN_Lung_Sounds.ipynb)

**Locally:**
```bash
pip install -r requirements.txt
jupyter lab BSN_Lung_Sounds.ipynb
```
The first cell downloads the workshop data (about 80 MB) from the Hugging Face dataset
[`AlirezaFB/ICBHI_2017`](https://huggingface.co/datasets/AlirezaFB/ICBHI_2017) (folder `workshop/`).
To use a local copy instead, set `BSN_DATA_DIR` to that folder before starting Jupyter.

## What's inside

| Section | Interactive controls |
|---|---|
| Listen to the data | recording, show/hide normal cycles, audio player |
| Filtering | sample rate, Butterworth type (none, low, high, band), cutoffs, order |
| Segmentation | duration, padding method, sample rate |
| Mel spectrogram | n_fft, hop, n_mels, fmax |
| Train a classifier | model, optimizer, learning rate, class weights |
| Results | Se, Sp, ICBHI score, accuracy, macro F1, per-class recall, confusion matrix |
| Export | ONNX file of the trained head plus a JSON description |

## Data

12 ICBHI recordings (3 per device) with their annotations, and frozen embeddings for ResNet-50,
EfficientNetV2-S, Swin-V2-B, VGGish, YAMNet and OPERA-CT on the official ICBHI train/test split.

Reference: B. M. Rocha et al., "An open access database for the evaluation of respiratory sound
classification algorithms," *Physiological Measurement*, 40(3), 035001, 2019.
