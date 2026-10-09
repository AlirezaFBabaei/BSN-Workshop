# Lung Sounds, End to End — IEEE BSN Workshop

An interactive notebook for a hands-on BSN workshop session on respiratory sound analysis,
built on **ICBHI 2017**. Attendees take a real recording from filter → segment → spectrogram →
classifier → ONNX, changing every setting with menus and sliders.

## Run it

**Colab** (what attendees do):
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AlirezaFBabaei/BSN-Workshop/blob/main/BSN_Lung_Sounds.ipynb)

Run the cells from top to bottom. Nothing to install; the notebook installs what it needs and
fetches the data.

**Locally:**

```bash
pip install -r requirements.txt
export BSN_DATA_DIR=/path/to/bsn_workshop_data     # Windows: set BSN_DATA_DIR=D:\...
jupyter notebook BSN_Lung_Sounds.ipynb
```

## Sections

| § | What it covers |
|---|---|
| 1 | Setup — install, locate data, load the manifest |
| 2 | Listen — 12 recordings, 4 devices, cycles coloured by class |
| 3 | Filtering — Butterworth low/high/band, before-and-after waveform, spectrum and audio; try your own filter |
| 4 | Segmentation — fixed-length cycles, reflect / zeros / repeat padding, truncation |
| 5 | Mel spectrogram — `n_fft`, `hop`, `n_mels`, `fmax`; try other time-frequency representations |
| 6 | Train — a small head on pre-computed embeddings of 5 backbones, no GPU; build your own head |
| 7 | Results — Se, Sp, ICBHI score, accuracy, macro F1, per-class recall, confusion matrix, all runs |
| 8 | Export — the head as ONNX (embedding in, 4 class probabilities out) |
| 9 | Auralis — upload the head to https://myauralis.pt/ and explore it with example-based XAI |

## Data

The notebook reads a bundle containing per-model embeddings, label files, 12 sample recordings
and a `manifest.json`. Point `BSN_DATA_DIR` at it, or let section 1 download it.

**The class order is read from `manifest.json` and never hard-coded.** For this dataset it is
`0 Normal, 1 Wheeze, 2 Crackle, 3 Both` — note that Wheeze and Crackle are the reverse of the
usual convention.

## Citation

Rocha, B. M. et al. (2019). An open access database for the evaluation of respiratory sound
classification algorithms. *Physiological Measurement*, 40(3), 035001.
