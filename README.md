# LENS
This is the official repository for "LENS: a mammography-specific hybrid CNN-Transformer with lesion-aware evidence modeling"

## Installation

### Option 1: local editable install

```bash
cd share/lens_hybridv5
python -m venv .venv
# Linux/macOS
source .venv/bin/activate
# Windows PowerShell
# .\.venv\Scripts\Activate.ps1

pip install -r requirements.txt
pip install -e .
```

### Option 2: direct usage from source

```bash
cd share/lens_hybridv5
python -m lens.example_usage
```

## Quick start

```python
import torch
from lens_hybridv5.hybridv5 import HybridV5, HybridV5Config

model = HybridV5(HybridV5Config(num_classes=3, image_size=448))
model.eval()

x = torch.randn(2, 3, 448, 448)
with torch.no_grad():
    logits = model(x)
    print(logits[0].shape if isinstance(logits, tuple) else logits.shape)
```

## Train a simple model

```bash
cd share/lens
python train.py --epochs 2 --batch-size 4 --learning-rate 1e-4 --save-path checkpoints/hybridv5_demo.pt
```

This script creates a tiny synthetic dataset and runs a short training loop to verify the model builds and updates correctly.

## Evaluate a checkpoint

```bash
cd share/lens
python eval.py --checkpoint checkpoints/hybridv5_demo.pt --batch-size 4
```

## Notes
- For real mammography experiments, replace the synthetic dataset with your own dataset loader and labels.

## License

This package is intended for research and code-sharing purposes. Please check the original project license before redistribution.

