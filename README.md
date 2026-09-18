# QuantFormer

### Quantum-Enhanced Transformer for Hyperspectral Image Classification

A hybrid quantum-classical Transformer for hyperspectral image classification, evaluated across six benchmark datasets with reproducibility experiments, ablation studies, statistical testing, and full-scene analysis.

<p align="center">

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge\&logo=python\&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-2.5.0-EE4C2C?style=for-the-badge\&logo=pytorch\&logoColor=white)
![PennyLane](https://img.shields.io/badge/PennyLane-0.42.3-6C4CC5?style=for-the-badge\&logo=pennylane\&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Scientific%20Computing-013243?style=for-the-badge\&logo=numpy\&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?style=for-the-badge\&logo=scikit-learn\&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-F37626?style=for-the-badge\&logo=jupyter\&logoColor=white)

</p>

---

## Overview

**QuantFormer** explores a hybrid quantum-classical Transformer architecture for hyperspectral image classification.

The model combines:

* Spatial tokenization of hyperspectral image patches
* Transformer-based feature representation
* A parameterized quantum circuit
* Quantum-enhanced feature transformation
* Classical classification layers
* Multi-seed evaluation for reproducibility

The complete experimental pipeline covers model validation, dataset preprocessing, reproduction experiments, cross-dataset evaluation, augmentation analysis, ablation studies, statistical testing, full-scene classification, and metric extraction.

---

## Key Specifications

| Component              | Configuration                        |
| ---------------------- | ------------------------------------ |
| Architecture           | Hybrid Quantum-Classical Transformer |
| Task                   | Hyperspectral Image Classification   |
| Transformer Layers     | 2                                    |
| Embedding Dimension    | 64                                   |
| Feed-Forward Dimension | 128                                  |
| Attention Heads        | 4                                    |
| Spatial Window         | 15 × 15                              |
| Spatial Tokens         | 225                                  |
| Quantum Qubits         | 4                                    |
| Quantum Layers         | 2                                    |
| Evaluation Seeds       | 42, 43, 44                           |
| Framework              | PyTorch + PennyLane                  |
| Quantum Simulation     | `default.qubit`, `lightning.qubit`   |

---

## Tech Stack

### Machine Learning & Quantum Computing

| Technology       | Purpose                                       |
| ---------------- | --------------------------------------------- |
| **Python**       | Core implementation                           |
| **PyTorch**      | Neural network and Transformer implementation |
| **PennyLane**    | Quantum machine learning integration          |
| **NumPy**        | Numerical computation                         |
| **scikit-learn** | Evaluation metrics and statistical analysis   |

### Experimentation & Visualization

| Technology             | Purpose                     |
| ---------------------- | --------------------------- |
| **Jupyter Notebook**   | Experimental pipeline       |
| **Matplotlib**         | Visualization               |
| **t-SNE**              | Feature-space visualization |
| **Confusion Matrices** | Classification analysis     |
| **McNemar's Test**     | Statistical comparison      |

### Hardware

The experiments were developed and evaluated using an **NVIDIA RTX A4500** GPU for classical GPU computation.

---

## Experimental Pipeline

The repository is organized into seven experimental phases.

| Phase       | Experiment                                                 |
| ----------- | ---------------------------------------------------------- |
| **Phase 0** | Quantum component validation and batched execution testing |
| **Phase 1** | Dataset preprocessing and pipeline preparation             |
| **Phase 2** | Indian Pines reproduction                                  |
| **Phase 3** | Pavia University reproduction                              |
| **Phase 4** | Extension to Salinas, KSC, and Botswana                    |
| **Phase 5** | Ablation studies and statistical testing                   |
| **Phase 6** | Houston 2013 full-scene evaluation                         |
| **Phase 7** | Full metrics, artifacts, and feature-space analysis        |

---

# Datasets

QuantFormer was evaluated on six hyperspectral benchmark datasets.

| Dataset              | Classes | Evaluation            |
| -------------------- | ------: | --------------------- |
| **Indian Pines**     |      16 | Patch classification  |
| **Pavia University** |       9 | Patch classification  |
| **Salinas**          |      16 | Patch classification  |
| **KSC**              |      13 | Patch classification  |
| **Botswana**         |      14 | Patch classification  |
| **Houston 2013**     |      15 | Full-scene evaluation |

> The original hyperspectral datasets are not included in this repository. Dataset files are excluded through `.gitignore`.

---

# Benchmark Results

## Indian Pines

Results across three evaluation seeds.

| Metric                |          Mean ± Std |
| --------------------- | ------------------: |
| Overall Accuracy (OA) |  **88.97% ± 0.93%** |
| Average Accuracy (AA) |  **78.34% ± 2.57%** |
| Cohen's Kappa         | **0.8742 ± 0.0106** |

---

## Pavia University

| Metric                |          Mean ± Std |
| --------------------- | ------------------: |
| Overall Accuracy (OA) |  **98.99% ± 0.42%** |
| Average Accuracy (AA) |  **98.33% ± 0.51%** |
| Cohen's Kappa         | **0.9865 ± 0.0056** |

---

## Cross-Dataset Evaluation

Mean results over three seeds.

| Dataset              |     OA |     AA |  Kappa |
| -------------------- | -----: | -----: | -----: |
| **Indian Pines**     | 88.97% | 78.34% | 0.8742 |
| **Pavia University** | 98.99% | 98.33% | 0.9865 |
| **Salinas**          | 99.26% | 99.48% | 0.9918 |
| **KSC**              | 96.48% | 94.23% | 0.9608 |
| **Botswana**         | 94.48% | 93.34% | 0.9402 |

---

# Augmentation Study

The effect of data augmentation was evaluated on three additional datasets.

| Dataset  | Setting              |     OA |     AA |  Kappa |
| -------- | -------------------- | -----: | -----: | -----: |
| Salinas  | Without Augmentation | 99.26% | 99.48% | 0.9918 |
| Salinas  | With Augmentation    | 98.90% | 98.98% | 0.9877 |
| KSC      | Without Augmentation | 96.48% | 94.23% | 0.9608 |
| KSC      | With Augmentation    | 97.56% | 95.67% | 0.9729 |
| Botswana | Without Augmentation | 94.48% | 93.34% | 0.9402 |
| Botswana | With Augmentation    | 96.08% | 95.19% | 0.9575 |

---

# Detailed Classification Metrics

Final extracted metrics from the evaluation pipeline.

| Dataset          | Precision | Recall / Balanced Acc. |     F1 |
| ---------------- | --------: | ---------------------: | -----: |
| Indian Pines     |    0.8442 |                 0.7835 | 0.8011 |
| Pavia University |    0.9763 |                 0.9836 | 0.9799 |
| Salinas          |    0.9958 |                 0.9955 | 0.9957 |
| KSC              |    0.9578 |                 0.9630 | 0.9593 |
| Botswana         |    0.9548 |                 0.9418 | 0.9470 |
| Houston 2013     |    0.7442 |                 0.7566 | 0.7393 |

The metrics above use the final extracted evaluation configuration and should not be directly interpreted as identical to the multi-seed OA/AA/Kappa benchmark protocol.

---

# Model Size & Inference

The quantum and corresponding classical mirror architectures have nearly identical parameter counts.

| Dataset          | QuantFormer Parameters | Classical Mirror |
| ---------------- | ---------------------: | ---------------: |
| Indian Pines     |                 34,984 |           34,960 |
| Pavia University |                 34,445 |           34,421 |
| Salinas          |                 34,900 |           34,876 |
| KSC              |                 34,705 |           34,681 |
| Botswana         |                 34,770 |           34,746 |
| Houston 2013     |                 34,835 |           34,811 |

The difference is **24 parameters** across the evaluated configurations.

### Approximate inference time

| Dataset          | ms / sample |
| ---------------- | ----------: |
| Indian Pines     |       0.298 |
| Pavia University |       0.279 |
| Salinas          |       0.277 |
| KSC              |       0.280 |
| Botswana         |       0.278 |
| Houston 2013     |       0.276 |

> Inference times are environment-specific measurements and should not be interpreted as hardware-independent benchmarks.

---

# Quantum Component

The quantum module uses a compact parameterized circuit integrated into the Transformer pipeline.

### Configuration

```text
Number of qubits      : 4
Quantum layers        : 2
Quantum backend       : PennyLane
Available simulators  : default.qubit, lightning.qubit
```

A Phase 0 execution test verified batched quantum processing rather than executing an independent quantum circuit for every token.

For a test containing **7,200 token vectors**, the implementation produced **one intercepted quantum execution call** with first-order derivatives enabled.

This validation was used to verify the intended batched execution design.

---

# Visual Results

The repository contains generated visualizations for the major experiments.

### Classification Maps

```text
figures/
├── classmap_botswana_full.png
├── classmap_houston2013_full15_full.png
├── classmap_indianpines_full.png
├── classmap_ksc_full.png
├── classmap_paviauniversity_full.png
└── classmap_salinas_full.png
```

### Confusion Matrices

```text
figures/
├── confmat_botswana_full.png
├── confmat_houston15_full.png
├── confmat_indianpines_full.png
├── confmat_ksc_full.png
├── confmat_pavia_full.png
└── confmat_salinas_full.png
```

### Additional Analysis

```text
figures/
├── phase1_preprocessing_summary.png
├── phase2_3_fidelity_checkpoints.png
├── phase4_augmentation_effect.png
├── phase5_ablation_heatmap.png
├── phase5_effect_sizes.png
├── phase6_houston15_summary.png
├── tsne_comparison_indianpines.png
└── tsne_comparison_paviauniversity.png
```

---

# Repository Structure

```text
QuantFormer/
│
├── artifacts/
│   ├── Botswana_artifacts.npz
│   ├── Houston2013_Full15_artifacts.npz
│   ├── IndianPines_artifacts.npz
│   ├── IndianPines_classical_artifacts.npz
│   ├── KSC_artifacts.npz
│   ├── PaviaUniversity_artifacts.npz
│   ├── PaviaUniversity_classical_artifacts.npz
│   └── Salinas_artifacts.npz
│
├── figures/
│   ├── classification maps
│   ├── confusion matrices
│   ├── ablation plots
│   ├── t-SNE visualizations
│   └── experiment summaries
│
├── phase0.ipynb
├── phase0_results.json
│
├── phase1_preprocessing.ipynb
├── phase1_report.json
│
├── phase2_indian_pines_reproduction.ipynb
├── phase2_indian_pines_results.json
│
├── phase3_pavia_university.ipynb
├── phase3_pavia_results.json
│
├── phase4_extension_datasets.ipynb
├── phase4_extension_results.json
│
├── phase5_ablation_study.ipynb
├── phase5_ablation_results.json
├── phase5_mcnemar_results.json
│
├── phase6_houston15.ipynb
├── phase6_houston15_results.json
├── phase6_mcnemar_results.json
│
├── phase7_extract_artifacts.ipynb
├── phase7_plotting.ipynb
├── phase7_full_metrics.json
└── phase7_separability_results.json
```

---

# Reproducibility

The experiments use fixed random seeds:

```text
42
43
44
```

The notebooks are organized sequentially according to the experimental phases.

For reproduction:

1. Install the required Python dependencies.
2. Download the required hyperspectral datasets separately.
3. Place datasets according to the preprocessing notebook configuration.
4. Run the notebooks in phase order.
5. Use the saved JSON files and generated figures for result verification.

The repository intentionally excludes the original datasets and large generated preprocessing files.

---

# Documentation

A complete project documentation file is included in the repository:

**`QuantFormer_Documentation.pdf`**

It provides additional details about the experimental methodology, implementation, evaluation procedures, and results.

---

# Limitations

The current implementation has several limitations:

* Quantum experiments are performed using simulated quantum backends rather than physical quantum hardware.
* The evaluated datasets vary substantially in spatial and spectral characteristics.
* Inference measurements are dependent on the development hardware and software environment.
* The reported results are experimental measurements and are not presented as state-of-the-art claims.
* Original hyperspectral datasets are not redistributed with the repository.

---

# Research Outputs

The project includes:

* Hybrid quantum-classical Transformer implementation
* Multi-dataset hyperspectral classification experiments
* Reproduction experiments
* Cross-dataset evaluation
* Data augmentation analysis
* Ablation studies
* Statistical significance testing
* Full-scene classification
* Confusion matrices
* Classification maps
* t-SNE feature-space analysis
* Extracted quantitative artifacts
* Reproducible experiment notebooks

---

# Citation

If you use this repository in academic work, please cite:

```bibtex
@software{anjum2026quantformer,
  author  = {Anjum, Amama},
  title   = {QuantFormer: Quantum-Enhanced Transformer for Hyperspectral Image Classification},
  year    = {2026},
  url     = {https://github.com/Ashley-33102/QuantFormer}
}
```

---

## Project Status

**Experimental pipeline completed.**

The repository currently contains the implementation notebooks, evaluation results, generated figures, extracted artifacts, and project documentation for the completed experimental pipeline.

---

<p align="center">

**QuantFormer — Hybrid Quantum-Classical Learning for Hyperspectral Image Classification**

</p>
