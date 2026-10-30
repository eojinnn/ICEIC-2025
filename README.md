# Robust Sound Source Localization Using CDR-Based Masking and CNN-Enhanced GCC-PHAT in Reverberant Environments

**Eojin Kim, Juseong Kim, Jungyu Choi, Joonwhi Kim, Sungbin Im** | Soongsil University | ICEIC 2025

[Paper](https://doi.org/10.1109/ICEIC64972.2025.10879682) | [Code](https://github.com/eojinnn/ICEIC-2025) | [Research Portfolio](https://github.com/eojinnn/Research-portfolio)

Research code combining CDR-based diffuseness masking, GCC-PHAT, and CNN regression for TDOA estimation.

![Proposed framework](https://github.com/user-attachments/assets/49b1d4fa-6c31-4681-9e5e-6d7227729d2c)

## Environment

Python with PyTorch, torchaudio, NumPy, librosa, Pyroomacoustics, scikit-learn, torchinfo and tqdm. Exact versions are not pinned.

## Data Preparation

Set the audio path in `data.py` (`LibriSpeechLocations.source_file`) and room/model settings in `cfg.py`.

## Training and Evaluation

The experiment driver is `main.py`; the proposed masking/CNN implementation is in `model.py`.

```bash
python main.py --exp_name my_experiment
```

**Note:** The checked-in `main.py` forces `args.evaluate = True`. For training, change this to `False`; evaluation requires a matching checkpoint at `experiments/my_experiment/model.pth`. This is research code, not a clean-environment verified release.

## Acknowledgements

The room simulation and training/evaluation pipeline are adapted from [Neural Generalized Cross Correlations (NGCC)](https://github.com/axeber01/ngcc). Its original [MIT license notice](LICENSES/NGCC-MIT.txt) is retained.

## Citation

```bibtex
@inproceedings{kim2025iceic,
  title={Robust Sound Source Localization Using CDR-Based Masking and CNN-Enhanced GCC-PHAT in Reverberant Environments},
  author={Kim, Eojin and Kim, Juseong and Choi, Jungyu and Kim, Joonwhi and Im, Sungbin},
  booktitle={2025 International Conference on Electronics, Information, and Communication (ICEIC)},
  year={2025},
  doi={10.1109/ICEIC64972.2025.10879682}
}
```
