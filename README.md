# Hybrid CNN-Transformer for Knee Osteoarthritis Classification

## Overview
Implementation of a hybrid architecture combining ResNet-50 
and Vision Transformer (ViT-Base) with cross-attention fusion 
for automated Kellgren-Lawrence (KL) grading of knee 
osteoarthritis from radiographs.

Paper: "A Hybrid CNN-Transformer Architecture for 
Interpretable Knee Osteoarthritis Diagnosis"
Journal: Scientific Reports (Under Review)

## Dataset
- Source: Kaggle Knee OA Dataset (Chen, P. 2018, Mendeley Data)
- Size: 8,260 radiographs (excluded AUTO_TEST split)
- Classes: 5 KL grades (0-4)
- Split: 70/10/20 (train/val/test)
- Link: https://www.kaggle.com/datasets/shashwatwork/knee-osteoarthritis-dataset-with-severity

## Requirements
See requirements.txt

## Usage
1. Upload notebook to Google Colab
2. Mount Google Drive
3. Run Cell 1-2 (setup + packages)
4. Run Cell 3-10 (data loading)
5. Run Cell 18 (ResNet-50 definition)
6. Run Cell 37-41 (Hybrid model training)
7. Run Cell 42-45 (model reload + evaluation)
8. Run Cell 46 (IoU + Latency analysis)
9. Run Cell 47-51 (results + visualization)
10. Run Cell 52-54 (XAI analysis)

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
"A Hybrid CNN-Transformer Architecture for Interpretable Knee Osteoarthritis Diagnosis." Scientific Reports (Under Review), 2025.

## License
MIT License
