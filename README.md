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

## Evaluate a checkpoint

```bash
cd share/lens
python eval.py --checkpoint checkpoints/hybridv5_demo.pt --batch-size 4
```

## Notes
- If you found this code useful, please cite our paper:
```
@article{Hoang2026,
  author = {Hoang, Duc Quy AND Cao, Van Kien AND Nguyen, Tan Nhu AND Nguyen, Ngoc Son},
  title = {LENS: A mammography-specific hybrid CNN-Transformer with lesion-aware evidence modeling},
  journal = {PLOS ONE},
  year = {2026},
  doi = {10.1371/journal.pone.0350720},
  publisher = {Public Library of Science},
  month = {09},
  volume = {21},
  url = {https://doi.org/10.1371/journal.pone.0350720},
  pages = {1-23},
  number = {9},
}
```
## License

The content in this repo is licensed under a Creative Commons Attribution 4.0 International license.

