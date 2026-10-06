# Lung Sounds, End to End — IEEE BSN Workshop

An interactive notebook for a hands-on BSN workshop session on respiratory sound analysis,
built on **ICBHI 2017**. Attendees take a real recording from filter → segment → spectrogram →
classifier → ONNX, changing every setting with menus and sliders.

## Run it

**Colab** (what attendees do): open `BSN_Lung_Sounds.ipynb`, run section 1, then go in order.
Nothing to install; the notebook installs what it needs and fetches the data.

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
| 3 | Filtering — Butterworth low/high/band, before-and-after waveform, spectrum and audio |
| 4 | Segmentation — fixed-length cycles, reflect / zeros / repeat padding, truncation |
| 5 | Mel spectrogram — `n_fft`, `hop`, `n_mels`, `fmax`, and the grey image a vision model sees |
| 6 | Train — a 2-layer head on pre-computed embeddings, 20 epochs, no GPU |
| 7 | Results — Se, Sp, ICBHI score, accuracy, macro F1, per-class recall, confusion matrix |
| 8 | Export — ONNX head with standardisation folded in, plus a JSON contract |
| 9 | Wrap-up — take-home points and discussion questions |

Each interactive section is followed by an empty ✏️ cell.

## Data

The notebook reads a bundle containing per-model embeddings, label files, 12 sample recordings
and a `manifest.json`. Point `BSN_DATA_DIR` at it, or let section 1 download it.

**The class order is read from `manifest.json` and never hard-coded.** For this dataset it is
`0 Normal, 1 Wheeze, 2 Crackle, 3 Both` — note that Wheeze and Crackle are the reverse of the
usual convention.

Two of the six embedding sets (`resnet50`, `efficientnet_v2_s`) are 1000-d ImageNet **logits**
rather than pooled features, because the head-removal step did not take effect for those
architectures. They are labelled as such in the model dropdown. See `FINDINGS.md` in the bundle.

## Citation

Rocha, B. M. et al. (2019). An open access database for the evaluation of respiratory sound
classification algorithms. *Physiological Measurement*, 40(3), 035001.
