# Robust Sound Source Localization Using CDR-Based Masking and CNN-Enhanced GCC-PHAT in Reverberant Environments

**ICEIC 2025** | **Eojin Kim, Juseong Kim, Jungyu Choi, Joonwhi Kim, Sungbin Im** | Soongsil University

[Published paper (DOI)](https://doi.org/10.1109/ICEIC64972.2025.10879682) | [Follow-up work: ICTCA 2025](https://github.com/eojinnn/ICTCA2025) | [Research portfolio](https://github.com/eojinnn/Research-portfolio)

A hybrid approach to **time difference of arrival (TDOA) estimation** in noisy and reverberant environments, combining spatial-coherence-based signal masking with GCC-PHAT and a CNN.

## Motivation

Conventional GCC-PHAT estimates the time delay between microphone signals from their cross-correlation. Its correlation peaks can become unreliable when reflections and background noise dominate. This work investigates whether **coherent-to-diffuse ratio (CDR) based masking** can improve the input representation before neural TDOA estimation.

## Method

**Two-channel audio → DOA-independent CDR estimate → binary diffuseness masking → GCC-PHAT features → CNN regression → estimated TDOA**

1. **CDR-based masking:** Estimate spatial coherence from two microphones, obtain a diffuseness estimate, and retain time-frequency components according to a binary threshold.
2. **GCC-PHAT:** Compute correlation features from the masked signals to represent candidate inter-microphone delays.
3. **CNN refinement:** Use a five-layer convolutional backbone followed by fully connected layers to regress the time delay.

![Overview of the CDR-based masking and CNN-enhanced GCC-PHAT method](https://github.com/user-attachments/assets/49b1d4fa-6c31-4681-9e5e-6d7227729d2c)

## Reported results

The conference paper evaluates simulated microphone signals produced with **Pyroomacoustics**, with different noise and reverberation conditions. For the **T60 = 0.6 s** comparison reported in Table II:

| Method | TDOA MAE (cm) ↓ |
| --- | ---: |
| Conventional GCC-PHAT | 1.40 |
| CNN-based parameterized GCC-PHAT (PGCC) | 1.01 |
| **CDR-masked GCC-PHAT + CNN (proposed)** | **0.94** |

These are **paper-reported results from simulated environments**, not measurements from a deployed localization system. The proposed approach is primarily motivated by performance under challenging acoustic conditions; the paper also notes that conventional GCC-PHAT can perform better in relatively favorable conditions.

## Code guide

| File | Purpose |
| --- | --- |
| [model.py](model.py) | GCC/PGCC modules, the **DiffusenessMask** module, and the CNN-based model |
| [data.py](data.py) | Speech loading and Pyroomacoustics room simulation |
| [cfg.py](cfg.py) | Microphone geometry, SNR/T60 ranges, and training parameters |
| [main.py](main.py) | Research training/evaluation entry point |
| [main_test.py](main_test.py) | Additional experiment and evaluation script |
| [dnn_models.py](dnn_models.py) | Supporting model components |

### Working with this research code

- The project requires external audio and a local Python/PyTorch environment with packages such as **torchaudio, librosa, pyroomacoustics, NumPy, scikit-learn, torchinfo, and tqdm**.
- **Important:** [data.py](data.py) contains an original local audio path (F: drive). Replace it with an appropriate audio file path before running. No source dataset is included here.
- Review [cfg.py](cfg.py) and the evaluation/checkpoint logic in [main.py](main.py); this repository is an experimental code snapshot rather than a verified one-command reproduction package.
- Published numerical results above were taken from the paper, not regenerated as part of this README update.

## Publication

**E. Kim, J. Kim, J. Choi, J. Kim, and S. Im**, "Robust Sound Source Localization Using CDR-Based Masking and CNN-Enhanced GCC-PHAT in Reverberant Environments," *International Conference on Electronics, Information, and Communication (ICEIC)*, 2025.

**DOI:** [10.1109/ICEIC64972.2025.10879682](https://doi.org/10.1109/ICEIC64972.2025.10879682)

The subsequent [ICTCA 2025 project](https://github.com/eojinnn/ICTCA2025) explores CDR-based enhancement and probabilistically weighted parameterized GCC-PHAT.
