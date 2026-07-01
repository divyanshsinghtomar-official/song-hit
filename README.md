<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/TensorFlow-2.x-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white" alt="TensorFlow">
  <img src="https://img.shields.io/badge/Keras-2.x-D00000?style=for-the-badge&logo=keras&logoColor=white" alt="Keras">
  <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="scikit-learn">
  <img src="https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="pandas">
  <img src="https://img.shields.io/badge/Matplotlib-11557c?style=for-the-badge&logo=python&logoColor=white" alt="Matplotlib">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-complete-brightgreen?style=flat-square" alt="Status">
  <img src="https://img.shields.io/badge/accuracy-~85%25-success?style=flat-square" alt="Accuracy">
  <img src="https://img.shields.io/badge/license-MIT-lightgrey?style=flat-square" alt="License">
  <img src="https://img.shields.io/badge/contributions-welcome-orange?style=flat-square" alt="Contributions">
</p>

<h1 align="center">
  Song Hit Predictor
</h1>

<p align="center">
  <b>Can we predict a hit song before it drops?</b><br>
  A deep learning approach to hit song science — using a <b>TensorFlow/Keras neural network</b> trained on audio features extracted from thousands of tracks.
</p>

---

## Overview

Every record label dreams of spotting the next *Billboard Hot 100* hit before anyone else. This project explores **hit song science** — the hypothesis that chart-topping songs share measurable acoustic DNA — by training a neural network to classify whether a song will be a hit based solely on its audio features.

> **Goal:** Build a binary classifier that predicts `is_hit` (1 = hit, 0 = non-hit) from features like tempo, key, mode, danceability, energy, valence, and more.

---

## Dataset

The dataset (`nn_ready.csv`) contains **thousands of tracks** with the following features:

| Feature | Description |
|---|---|
| **tempo** | Beats per minute (BPM) — the speed of the track |
| **key** | Musical key (0=C, 1=C#, ... 11=B) |
| **mode** | Major (1) or Minor (0) |
| **danceability** | How suitable the track is for dancing (0-1) |
| **energy** | Perceptual intensity and activity (0-1) |
| **valence** | Musical positiveness / mood (0-1) |
| **acousticness** | Whether the track is acoustic (0-1) |
| **speechiness** | Presence of spoken words (0-1) |
| **liveness** | Likelihood of a live audience recording (0-1) |
| **loudness** | Overall loudness in dB |
| **duration_ms** | Track length in milliseconds |
| **popularity** | Popularity score (0-100) |
| **is_hit** | **Target** — 1 if hit, 0 if non-hit |

---

## Model Architecture

A fully-connected **feedforward neural network** built with TensorFlow/Keras:

```
┌──────────┐
│  Input   │  (12 features)
└────┬─────┘
     │
┌────▼─────┐
│  Dense   │  10 units, ReLU
└────┬─────┘
     │
┌────▼─────┐
│  Dense   │  10 units, ReLU
└────┬─────┘
     │
┌────▼─────┐
│  Dense   │  1 unit, Sigmoid 
└──────────┘
```

**Training details:**
- **Loss:** Binary Crossentropy
- **Optimizer:** Adam
- **Epochs:** 20
- **Validation split:** 20%
- **Features:** 12 input dimensions
- **Output:** Binary classification (hit / non-hit)

---

## Exploratory Analysis & Charts

### 1. BPM Over Decades
*How tempo has evolved across decades — are we dancing faster or slower?*

<img src="charts/01_bpm_over_decades.png" alt="BPM Over Decades" width="700"/>

---

### 2. Valence Over Time
*The emotional tone of hits through the years — are we getting happier or sadder?*

<img src="charts/02_valence_over_time.png" alt="Valence Over Time" width="700"/>

---

### 3. Key Distribution
*Which musical keys produce the most hits?*

<img src="charts/03_key_distribution.png" alt="Key Distribution" width="700"/>

---

### 4. Major vs. Minor
*Do hit songs lean major or minor? The classic mode battle.*

<img src="charts/04_major_vs_minor.png" alt="Major vs Minor" width="700"/>

---

### 5. The Loudness War
*Are songs getting progressively louder over time?*

<img src="charts/05_loudness_war.png" alt="Loudness War" width="700"/>

---

### 6. Danceability Over Time
*Are we making music that makes us move more than ever?*

<img src="charts/06_danceability_over_time.png" alt="Danceability Over Time" width="700"/>

---

### 7. Hits vs. Non-Hits Comparison
*A side-by-side comparison of audio features between chart-toppers and the rest.*

<img src="charts/07_hits_vs_nonhits_comparison.png" alt="Hits vs Non-Hits" width="700"/>

---

### 8. Feature Importance
*Which features matter most when predicting a hit?*

<img src="charts/08_feature_importance.png" alt="Feature Importance" width="700"/>

---

### 9. Model Performance — Confusion Matrix
*How well did our classifier separate hits from non-hits?*

<img src="charts/09_confusion_matrix.png" alt="Confusion Matrix" width="600"/>

---

## Quickstart

```bash
# Clone the repo
git clone https://github.com/divyanshsinghtomar-official/song-hit.git
cd song-hit

# Install dependencies
pip install tensorflow pandas numpy matplotlib scikit-learn

# Launch the notebook
jupyter notebook hit.ipynb
```

Run all cells in `hit.ipynb` to train the model from scratch and reproduce the analysis.

---

## Project Structure

```
song-hit/
├── hit.ipynb              # Main notebook — training & analysis
├── nn_ready.csv           # Preprocessed dataset
├── charts/                # Generated visualizations
│   ├── 01_bpm_over_decades.png
│   ├── 02_valence_over_time.png
│   ├── 03_key_distribution.png
│   ├── 04_major_vs_minor.png
│   ├── 05_loudness_war.png
│   ├── 06_danceability_over_time.png
│   ├── 07_hits_vs_nonhits_comparison.png
│   ├── 08_feature_importance.png
│   └── 09_confusion_matrix.png
└── README.md              # You are here
```

---

## Results

The neural network achieves **~85% accuracy** on the test set, demonstrating that audio features contain genuine predictive signal for hit song classification. Key insights:

- **Valence & Danceability** are among the strongest predictors
- **Loudness** has increased systematically over decades (the loudness war is real)
- **Key & Mode** show clustering but not decisive separation
- Hit songs cluster in specific feature ranges — there *is* a formula

---

## Contributing

Have an idea to improve the model? Want to add more features (genre, artist, lyrics sentiment)? Contributions are welcome! Open an issue or submit a PR.

---

## License

MIT — free to use, modify, and share.

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/divyanshsinghtomar-official">Divyansh Singh Tomar</a>
</p>
<p align="center">
  <a href="https://www.youtube.com/@greencode-">
    <img src="https://img.shields.io/badge/YouTube-Green%20Code-FF0000?style=flat-square&logo=youtube&logoColor=white" alt="YouTube">
  </a>
</p>
