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

## Usage - Run Complete Pipeline
Open `Knee_Osteoarthritis_Main_Code.ipynb` in Google Colab:

**Setup & Data (Cells 1-10):**
- Cell 1: Mount Google Drive
- Cell 2: Install packages (timm, grad-cam)
- Cell 3: Import libraries + set random seeds
- Cell 4: Dataset path setup
- Cells 5-7: Dataset exploration + visualization
- Cell 8: Custom dataset class
- Cell 9: Data augmentation transforms
- Cell 10: Create DataLoaders

**Baseline Models Training (Cells 11-36):**
- Cells 11-14: EfficientNet-B0
- Cells 15-17: ConvNeXt
- Cells 18-21: ResNet-50 Baseline
- Cells 22-25: DenseNet-161
- Cells 26-29: Swin Transformer
- Cells 30-36: Evaluation + visualization

**Hybrid Model Training (Cells 37-41):**
- Cell 37: ViT Branch definition
- Cell 38: CNN Branch definition
- Cell 39: Cross-Attention Fusion module
- Cell 40: Complete Hybrid model
- Cell 41: Train Hybrid model

**Evaluation Only - Skip Training (Cells 42-51):**
- Cell 42: Dataset class (reload)
- Cell 43: ResNet50 definition (reload)
- Cell 44: Hybrid model definition (reload)
- Cell 45: Load pretrained models
- Cell 46: IoU expansion (150 samples) + inference latency
- Cell 47: Evaluate both models on test set
- Cell 48: Extract variables for visualization
- Cell 49: Generate all visualizations
- Cell 50: Export results to CSV
- Cell 51: Final summary report

**Explainability Analysis (Cells 52-54):**
- Cell 52: Grad-CAM visualization
- Cell 53: Attention Rollout
- Cell 54: XAI comparison + IoU calculation

## Results
| Model | QWK | Accuracy | Macro F1 |
|-------|-----|----------|----------|
| ResNet-50 Baseline | 0.8353±0.0088 | 65.59% | 0.6840 |
| Hybrid CNN-Transformer | 0.8368±0.0055 | 65.67% | 0.6855 |
| Swin Transformer | 0.8580 | 69.69% | 0.7240 |
| ConvNeXt-Base | 0.8552 | 68.48% | 0.7258 |
| DenseNet-161 | 0.8493 | 67.57% | 0.6892 |
| EfficientNet-B0 | 0.8311 | 65.70% | 0.6744 |

See results/ folder for detailed CSV files.

## Statistical Validation
- 4 independent runs (seeds: 42, 123, 456, 789)
- Paired t-test: t=0.197, p=0.857 (not significant)
- IoU analysis: 150 test samples, mean=0.0186±0.0243

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
