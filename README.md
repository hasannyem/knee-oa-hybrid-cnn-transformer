# Hybrid CNN-Transformer for Knee Osteoarthritis Classification

## Overview
Implementation of a hybrid architecture combining ResNet-50 and Vision Transformer (ViT-Base) with cross-attention fusion for automated Kellgren-Lawrence (KL) grading of knee osteoarthritis from radiographs.

Paper: "A Hybrid CNN-Transformer Architecture for Interpretable Knee Osteoarthritis Diagnosis"
Journal: Scientific Reports (Under Review)

## Dataset
- Source: Kaggle Knee OA Dataset (Chen, P. 2018, Mendeley Data)
- Size: 8,260 radiographs (excluded AUTO_TEST split)
- Classes: 5 KL grades (0-4)
- Split: 70/10/20 (train/val/test)
- Link: https://www.kaggle.com/datasets/shashwatwork/knee-osteoarthritis-dataset-with-severity

## Requirements
See requirements.txt

## Repository Structure

```
knee-oa-hybrid-cnn-transformer/
├── Knee_OA_Training.ipynb      # Training (Google Colab + GPU)
├── Knee_OA_Evaluation.ipynb    # Evaluation (Local PC / CPU)
├── requirements.txt
├── results/                    # CSV results files
└── figures/                    # Generated figures
```

## Usage

### Step 1: Dataset Setup
Download dataset from Kaggle:  
https://www.kaggle.com/datasets/shashwatwork/knee-osteoarthritis-dataset-with-severity

Upload to Google Drive with this structure:
MyDrive/knee/data/
├── train/  (0/, 1/, 2/, 3/, 4/)
├── val/    (0/, 1/, 2/, 3/, 4/)
└── test/   (0/, 1/, 2/, 3/, 4/)
Create output folder: `MyDrive/knee/outputs/`

---

### Step 2: Model Training (Google Colab + GPU)
Open `Knee_OA_Training.ipynb` in Google Colab.  
Enable GPU: **Runtime → Change runtime type → T4 GPU**

| Cells | Task |
|-------|------|
| 1–10  | Setup, data loading, preprocessing |
| 11–14 | Train EfficientNet-B0 |
| 15–17 | Train ConvNeXt |
| 18–21 | Train ResNet-50 Baseline (4 seeds) |
| 22–25 | Train DenseNet-161 |
| 26–29 | Train Swin Transformer |
| 30–34 | Train Hybrid CNN-Transformer (4 seeds) |
| 35–39 | Train Ablation model + XAI analysis |

All trained models saved to: `MyDrive/knee/outputs/`

---

### Step 3: Download Models
Download all `.pth` files from Google Drive to local PC:
local_models/
├── best_model.pth
├── best_model_seed123.pth
├── best_model_seed456.pth
├── best_model_seed789.pth
├── best_hybrid_model.pth
├── best_hybrid_model_seed123.pth
├── best_hybrid_model_seed456.pth
├── best_hybrid_model_seed789.pth
├── best_efficientnet_model.pth
├── best_convnext_model.pth
├── best_densenet_model.pth
├── best_swin_model.pth
└── best_ablation_concat_model.pth
### Step 4: Evaluation (Local PC — CPU)
Open `Knee_OA_Evaluation.ipynb` in Jupyter Notebook.

Update paths in **Cell 3**:
```python
MODEL_DIR = Path(r"your/path/to/models")
DATA_DIR  = Path(r"your/path/to/data")
```
Run all cells. Results and figures saved to `MODEL_DIR/results/`


## Hardware
- GPU: NVIDIA T4 (Google Colab Pro)
- Framework: PyTorch 2.0, CUDA 11.8
- Note: Results may vary slightly on different hardware

## Citation
If you use this code, please cite:
[Rana Muhammad Zain Ul Abideen, Md Nyem Hasan Bhuiyan, Naveed Anwer Butt, Imran Ashraf, Daniel Gavilanes, Manuel Masias Vergara]. 
"A Hybrid CNN-Transformer Architecture for Interpretable Knee Osteoarthritis Diagnosis." Scientific Reports (Under Review), 2026.

## License
MIT License
