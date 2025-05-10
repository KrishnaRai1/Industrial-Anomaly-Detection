# Industrial Anomaly Detection: Comparative Analysis of Advanced Methods

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1-KM-aORwoAhRB-wr2rZM3pO6WgNo1jew)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1C9VBAlsOP1mlrgGMsq1b3FHB1D7qDsDv?usp=sharing)

This repository contains implementations and analyses of state-of-the-art industrial anomaly detection methods, with a focus on **PatchCore** and **DRAEM**, evaluated on benchmark datasets including MVTec AD and Severstal Steel Defect Detection.

## Research Report
The complete research paper is available in [docs/Industrial_Anomaly_Detection_Analysis.pdf](docs/Industrial_Anomaly_Detection_Analysis.pdf)

##  Key Implementations
1. **PatchCore** (Section 2 of report)
   - Memory-based approach using locally aware patch features
   - Coreset subsampling for efficient memory usage
2. **DRAEM** (Section 3 of report)
   - Discriminatively trained reconstruction embedding
   - Synthetic anomaly generation using DTD textures
3. **Severstal Steel Analysis** (Section 3 extension)
   - Evaluation on real-world industrial dataset
   - Handling extreme class imbalance (1000:1 ratio)
  
## Key Contributions
1. Comparative analysis of 4 major anomaly detection paradigms
2. Implementation guidelines for real-time deployment
3. Empirical evaluation of synthetic anomaly generation techniques
4. Computational efficiency benchmarks for industrial applications

## Implemented Methods

### 1. PatchCore (Section 2)
**Key Results**:
| Metric | MVTec (Bottle) | Autoencoder |
|--------|----------------|-------------|
| AUROC  | 87.45%         | 69.23%      |
| Recall | 98.25%         | 69.23%      |
| Inference Time | 0.22s/img | 0.03s/img |

### 2. DRAEM (Section 3)
**Performance**:
| Dataset | Image AUROC | Pixel AUROC | F1-Score |
|---------|-------------|-------------|----------|
| MVTec   | 93.89%      | 83.65%      | 0.8421   |
| Severstal| -           | -           | 0.8421   |

**DTD Impact Analysis**:
| Configuration | Pixel AUROC | Image AUROC | F1-Score |
|---------------|-------------|-------------|----------|
| With DTD      | 0.8365      | 0.9389      | 0.8421   |
| Synthetic Only| 0.7923      | 0.8912      | 0.7856   |

### 3. Isolation Forest (Section 4)
**Benchmarks**:
| Dataset | Precision | Recall | Inference Time |
|---------|-----------|--------|----------------|
| MVTec   | 85%       | 80%    | 0.03s/sample   |
| DAGM    | 91%       | 89%    | 0.04s/sample   |

## Repository Structure
industrial-anomaly-detection/
├── notebooks/
│ ├── 01_patchcore_draem.ipynb # PatchCore & DRAEM implementation
│ └── 02_draem_severstal.ipynb # DRAEM & Severstal analysis
├── images/
│ ├── patchcore/ # ROC curves, heatmaps
│ ├── draem/ # Reconstructions, anomaly maps
├── docs/
│ └── Industrial_Anomaly_Detection_Analysis.pdf
└── data/ # Dataset access instruction

## Datasets
**Preprocessed Datasets**:
- [Bottle Dataset](https://drive.google.com/drive/folders/1Lcw8tILhnZXnQ472NdfTSvwvHjrQEW-9)
- [DTD Textures](https://drive.google.com/drive/folders/1D_dASZICmsFPaRtNXzBqdc3L4utpYx5V)
- [MVTec Subset](https://drive.google.com/drive/folders/1WWBiVh5KZ1GbI5dyULOnGjYXxZM3PMC0)
- [DAGM Preprocessed](https://drive.google.com/drive/folders/1OPSJpZEfpoBYgM68Yfpes_JMkqnHRQCj)

##  Getting Started
1. Clone repository: git clone https://github.com/KrishnaRai1/Industrial-Anomaly-Detection.git
2. Mount Google Drive in Colab:
  from google.colab import drive
  drive.mount('/content/drive')
3. Update paths in notebooks to match your Drive folder structure.

## Computational Benchmarks
Method | Training Time | Inference Time | Memory
-------|---------------|----------------|--------
PatchCore | N/A | 0.22s/img | 4.2GB
DRAEM | 68min | 0.42s/img | 3.8GB
Autoencoder | 45min | 0.03s/img | 1.1GB

##  Key Findings (From Research Paper)
1. **DTD Enhancement**: Using DTD textures improved DRAEM's pixel AUROC by 5.6% compared to synthetic textures
2. **Severstal Challenge**: Achieved 98.25% recall but only 4.76% specificity on steel defects
3. **PatchCore Limitations**: 12.8% lower AUROC than original paper due to computational constraints
4. **Hybrid Approaches**: Combining reconstruction and memory-based methods showed promise

## Citation
@misc{krishna2025industrial,
  author = {Krishna},
  title = {Industrial Anomaly Detection Analysis},
  year = {2025},
  howpublished = [Industrial Anomaly Detection Analysis](https://github.com/KrishnaRai1/Industrial-Anomaly-Detection)
}

## License
This project is released for academic use only. Dataset usage must comply with original licenses:
- MVTec AD: CC-BY-NC-SA 4.0
- Severstal: CC0 1.0 Universal
