# MONAI Hands‑On Demonstrations

Practical, straight‑to‑the‑point demonstrations of MONAI (Medical Open Network for AI) using a single self‑contained Jupyter notebook.

## What’s inside

The notebook `MONAI.ipynb` includes:
- Basic medical image loading and preprocessing with MONAI transforms
- Data augmentation for medical images
- 2D classification with DenseNet121
- 3D segmentation with U‑Net
- Medical imaging metrics (Dice, Hausdorff, confusion matrix)
- Model zoo architectures (DenseNet, ResNet, EfficientNet, U‑Net, SegResNet, UNETR)
- MONAI Bundles overview (pretrained models and configs)
- Advanced preprocessing (windowing, normalization, thresholding, augmentations)

## Requirements

- Python 3.9+
- PyTorch
- MONAI
- matplotlib
- scikit‑image

Install from `requirements.txt` (CPU example):

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\\Scripts\\activate
pip install -r requirements.txt
```

Note: For GPU, install the correct PyTorch build for your CUDA version: https://pytorch.org/get-started/locally/

## Run

```bash
# Activate your environment first
jupyter lab  # or: jupyter notebook
```
Open `MONAI.ipynb` and run cells top‑to‑bottom. The notebook uses synthetic data, so it runs offline without downloads.

## Using your own data

- Replace synthetic arrays with your files (DICOM/NIfTI) and use MONAI’s dictionary transforms:
  - Create samples like: `{ "image": <ndarray>, "label": <int/ndarray> }`
  - Add a channel dimension (C, ...): `(H, W) -> (1, H, W)` or `(D, H, W) -> (1, D, H, W)`
  - Use `...d` transforms (e.g., `ScaleIntensityd`, `Resized`) with `keys=["image", …]`

## Troubleshooting

- ValueError: Unsupported output type: <class 'dict'> → Use dictionary transforms (`...d`) with `keys`.
- EnsureChannelFirst error (metadata) → Manually add channel or use `EnsureChannelFirstd(keys=["image"])`.
- 3D OOM → Lower batch size, reduce UNet channels, or use smaller volumes.

## License

Specify your project license here (e.g., MIT).
