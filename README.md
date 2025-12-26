
---

# Wireless ML Modulation Classification

This repository implements an **industry-style modulation classification pipeline** using **machine learning on baseband IQ signals**.
The project focuses on **clean data generation, realistic impairments, and reproducible evaluation**, following practices used in modern wireless systems.

**Current scope:** automatic classification of **BPSK, QPSK, 16-QAM, and 64-QAM** under noisy and impaired channels.

---

## Project Structure

```
wireless-ml-modulation-classification/
├── src/        # core library (dataset, modulations, models, evaluation)
├── scripts/    # runnable entrypoints (generate, train, evaluate)
├── tests/      # unit tests
├── data/       # generated datasets (gitignored)
├── results/    # experiment outputs (gitignored)
```

* `src/` contains reusable, importable code
* `scripts/` contains experiment entrypoints
* `data/` and `results/` are generated locally and not tracked by Git

---

## Modulation Schemes

The current implementation supports the following modulation formats:

* BPSK
* QPSK
* 16-QAM
* 64-QAM

This set reflects **industry-relevant digital modulation schemes** used in modern wireless communication systems.

---

## Signal & Channel Model (High-Level)

The dataset generation pipeline follows this structure:

1. Bit generation and symbol mapping
2. Pulse shaping using **root-raised cosine (RRC)** filtering
3. Channel and impairments:

   * AWGN over a configurable SNR range
   * Random carrier frequency offset (CFO)
   * Random phase offset
   * (Optional extensions: Rayleigh fading, IQ imbalance)
4. Fixed-length IQ window extraction (e.g., 1024 complex samples)

Each sample is stored along with its **label and impairment metadata** to support reproducible evaluation.

---

## How to Run (Basic)

### Generate dataset

```bash
python scripts/gen_dataset.py
```

Generated datasets are saved under:

```
data/
```

### Train model

```bash
python scripts/train.py
```

Training outputs (models, metrics, plots) are saved under:

```
results/
```

### Evaluate model

```bash
python scripts/eval.py
```

---

## Reproducibility

* All datasets and results are generated locally
* Random seeds and channel parameters are logged per run
* No generated data is committed to the repository

---

## Roadmap (Planned Extensions)

* Add 256-QAM
* Robust evaluation under fading channels
* Feature-based baselines (SVM / RF)
* Improved generalization testing across impairments

---

## License

No License

---


