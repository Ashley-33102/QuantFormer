\# QuantFormer



\### Quantum-Enhanced Transformer for Hyperspectral Image Classification



QuantFormer is a \*\*hybrid quantum-classical Transformer\*\* for hyperspectral image (HSI) classification. The project investigates the integration of a compact parameterized quantum circuit into a Transformer-based classification pipeline and evaluates the resulting model across multiple hyperspectral benchmarks.



The experimental workflow covers architecture validation, preprocessing, benchmark reproduction, cross-dataset evaluation, augmentation analysis, ablation studies, statistical testing, full-scene inference, and feature-separability analysis.



> \*\*Project status:\*\* Experimental pipeline completed across six HSI datasets, with quantitative results, visualizations, statistical analyses, and extracted artifacts preserved in the repository.



\---



\## Overview



Hyperspectral images contain hundreds of spectral bands, providing rich information for distinguishing land-cover classes. However, their high dimensionality, limited labeled samples, and strong spectral-spatial correlations make classification challenging.



QuantFormer explores whether a \*\*small quantum computational component\*\* can be integrated into a Transformer architecture while maintaining a compact overall parameter count.



The model combines:



\* Spectral-spatial HSI representations

\* Transformer-based feature processing

\* Multi-head self-attention

\* A parameterized quantum circuit

\* Classical neural network components

\* Multi-dataset evaluation

\* Statistical and ablation analysis



The quantum component is evaluated using \*\*simulated quantum backends\*\*, rather than physical quantum hardware.



\---



\## Model Configuration



| Component              |                        Configuration |

| ---------------------- | -----------------------------------: |

| Architecture           | Hybrid Quantum-Classical Transformer |

| Transformer Layers     |                                    2 |

| Embedding Dimension    |                                   64 |

| Feed-Forward Dimension |                                  128 |

| Attention Heads        |                                    4 |

| Spatial Window         |                              15 × 15 |

| Spatial Tokens         |                                  225 |

| Quantum Qubits         |                                    4 |

| Quantum Layers         |                                    2 |

| Task                   |   Hyperspectral Image Classification |

| Evaluation Seeds       |                           42, 43, 44 |



The quantum component is deliberately compact. Depending on the dataset configuration, the complete model contains approximately \*\*34–35K trainable parameters\*\*.



\---



\## Experimental Pipeline



The project is organized into sequential experimental phases.



| Phase       | Experiment                                                                          |

| ----------- | ----------------------------------------------------------------------------------- |

| \*\*Phase 0\*\* | Architecture, tensor-shape, quantum execution, and gradient validation              |

| \*\*Phase 1\*\* | Dataset preprocessing and standardized input preparation                            |

| \*\*Phase 2\*\* | Indian Pines benchmark reproduction                                                 |

| \*\*Phase 3\*\* | Pavia University evaluation                                                         |

| \*\*Phase 4\*\* | Cross-dataset extension with Salinas, KSC, and Botswana                             |

| \*\*Phase 5\*\* | Ablation study and statistical comparison                                           |

| \*\*Phase 6\*\* | Houston 2013 full-scene evaluation                                                  |

| \*\*Phase 7\*\* | Full metrics, artifact extraction, feature visualization, and separability analysis |



\---



\## Datasets



QuantFormer was evaluated across six hyperspectral benchmarks:



| Dataset          | Classes | Evaluation                      |

| ---------------- | ------: | ------------------------------- |

| Indian Pines     |      16 | Multi-seed benchmark evaluation |

| Pavia University |       9 | Multi-seed benchmark evaluation |

| Salinas          |      16 | Multi-seed evaluation           |

| KSC              |      13 | Multi-seed evaluation           |

| Botswana         |      14 | Multi-seed evaluation           |

| Houston 2013     |      15 | Full-scene evaluation           |



The original datasets are \*\*not included\*\* in this repository. Dataset files and other large local preprocessing outputs are excluded through `.gitignore`.



\---



\# Results



\## Benchmark Performance



Results below are taken directly from the experiment result files stored in the repository.



\### Multi-seed benchmark results



| Dataset              |                 OA |                 AA |           Cohen's κ |

| -------------------- | -----------------: | -----------------: | ------------------: |

| \*\*Indian Pines\*\*     | \*\*88.97% ± 0.93%\*\* | \*\*78.34% ± 2.57%\*\* | \*\*0.8742 ± 0.0106\*\* |

| \*\*Pavia University\*\* | \*\*98.99% ± 0.42%\*\* | \*\*98.33% ± 0.51%\*\* | \*\*0.9865 ± 0.0056\*\* |



For Pavia University, the recorded OA remained within \*\*1 percentage point across the three evaluation seeds\*\*.



\### Cross-dataset extension



The Phase 4 experiment evaluates the effect of augmentation across three additional datasets.



| Dataset      | Setting     | Mean OA | Mean AA | Mean κ |

| ------------ | ----------- | ------: | ------: | -----: |

| \*\*Salinas\*\*  | Unaugmented |  99.26% |  99.48% | 0.9918 |

| \*\*Salinas\*\*  | Augmented   |  98.90% |  98.98% | 0.9877 |

| \*\*KSC\*\*      | Unaugmented |  96.48% |  94.23% | 0.9608 |

| \*\*KSC\*\*      | Augmented   |  97.56% |  95.67% | 0.9729 |

| \*\*Botswana\*\* | Unaugmented |  94.48% |  93.34% | 0.9402 |

| \*\*Botswana\*\* | Augmented   |  96.08% |  95.19% | 0.9575 |



The augmentation experiment therefore shows \*\*dataset-dependent effects\*\* rather than a uniform improvement across all benchmarks.



\---



\## Full Metric Evaluation



Phase 7 additionally computes macro and weighted classification metrics.



| Dataset          | Macro Precision | Macro Recall | Macro F1 | Balanced Accuracy |

| ---------------- | --------------: | -----------: | -------: | ----------------: |

| Indian Pines     |          84.42% |       78.35% |   80.11% |            78.35% |

| Pavia University |          97.63% |       98.36% |   97.99% |            98.36% |

| Salinas          |          99.58% |       99.55% |   99.57% |            99.55% |

| KSC              |          95.78% |       96.30% |   95.93% |            96.30% |

| Botswana         |          95.48% |       94.18% |   94.70% |            94.18% |

| Houston 2013     |          74.42% |       75.66% |   73.93% |            75.66% |



These metrics provide additional information about class imbalance and per-class behavior beyond overall accuracy.



\---



\## Parameter Count



The Phase 7 artifact extraction records the following parameter counts:



| Dataset          | Full Configuration | Classical Mirror | Difference |

| ---------------- | -----------------: | ---------------: | ---------: |

| Indian Pines     |             34,984 |           34,960 |         24 |

| Pavia University |             34,445 |           34,421 |         24 |

| Salinas          |             34,900 |           34,876 |         24 |

| KSC              |             34,705 |           34,681 |         24 |

| Botswana         |             34,770 |           34,746 |         24 |

| Houston 2013     |             34,835 |           34,811 |         24 |



The quantum configuration therefore introduces a very small parameter-count difference relative to the corresponding classical mirror configuration.



\---



\## Recorded Inference Time



Phase 7 records approximately \*\*0.28–0.30 ms per sample\*\* under the evaluation environment:



| Dataset          | Inference Time / Sample |

| ---------------- | ----------------------: |

| Indian Pines     |                0.298 ms |

| Pavia University |                0.279 ms |

| Salinas          |                0.277 ms |

| KSC              |                0.280 ms |

| Botswana         |                0.278 ms |

| Houston 2013     |                0.276 ms |



These values are \*\*environment-specific measurements\*\*, not hardware-independent benchmarks.



\---



\# Visual Results



The repository contains generated figures for qualitative and quantitative inspection.



\### Classification Maps



\* Indian Pines

\* Pavia University

\* Salinas

\* KSC

\* Botswana

\* Houston 2013



\### Confusion Matrices



Confusion matrices are provided for the evaluated benchmark datasets.



\### Feature Analysis



The repository includes t-SNE comparisons for:



\* Indian Pines

\* Pavia University



These visualizations are used to inspect feature-space separability.



\### Ablation Analysis



Phase 5 includes:



\* Ablation heatmap

\* Effect-size visualization

\* Statistical comparison results



\### Additional Analysis



Phase-specific figures include:



\* Preprocessing summary

\* Fidelity checkpoints

\* Augmentation effects

\* Houston 2013 summary

\* Full-scene class maps

\* Confusion matrices

\* Feature-separability visualizations



\---



\## Repository Structure



```text

QuantFormer/

│

├── artifacts/

│   ├── Botswana\_artifacts.npz

│   ├── Houston2013\_Full15\_artifacts.npz

│   ├── IndianPines\_artifacts.npz

│   ├── IndianPines\_classical\_artifacts.npz

│   ├── KSC\_artifacts.npz

│   ├── PaviaUniversity\_artifacts.npz

│   ├── PaviaUniversity\_classical\_artifacts.npz

│   └── Salinas\_artifacts.npz

│

├── figures/

│   ├── classmap\_\*.png

│   ├── confmat\_\*.png

│   ├── phase1\_preprocessing\_summary.png

│   ├── phase2\_3\_fidelity\_checkpoints.png

│   ├── phase4\_augmentation\_effect.png

│   ├── phase5\_ablation\_heatmap.png

│   ├── phase5\_effect\_sizes.png

│   ├── phase6\_houston15\_summary.png

│   ├── tsne\_comparison\_indianpines.png

│   └── tsne\_comparison\_paviauniversity.png

│

├── phase0.ipynb

├── phase0\_results.json

│

├── phase1\_preprocessing.ipynb

├── phase1\_report.json

│

├── phase2\_indian\_pines\_reproduction.ipynb

├── phase2\_indian\_pines\_results.json

│

├── phase3\_pavia\_university.ipynb

├── phase3\_pavia\_results.json

│

├── phase4\_extension\_datasets.ipynb

├── phase4\_extension\_results.json

│

├── phase5\_ablation\_study.ipynb

├── phase5\_ablation\_results.json

├── phase5\_mcnemar\_results.json

│

├── phase6\_houston15.ipynb

├── phase6\_houston15\_results.json

├── phase6\_mcnemar\_results.json

│

├── phase7\_extract\_artifacts.ipynb

├── phase7\_plotting.ipynb

├── phase7\_full\_metrics.json

├── phase7\_separability\_results.json

│

├── QuantFormer\_Documentation.pdf

├── .gitignore

└── README.md

```



\---



\# Reproducibility



\## Environment



The experiments were developed using:



\* Python 3.10

\* PyTorch

\* PennyLane

\* NumPy

\* SciPy

\* scikit-learn

\* Matplotlib

\* Jupyter



The recorded development environment used an \*\*NVIDIA RTX A4500\*\* for classical GPU computation, while the quantum component was evaluated through simulated quantum backends.



\## Running the Experiments



The notebooks are organized sequentially by phase.



For example:



```text

Phase 0

&#x20;  ↓

Phase 1

&#x20;  ↓

Phase 2

&#x20;  ↓

Phase 3

&#x20;  ↓

Phase 4

&#x20;  ↓

Phase 5

&#x20;  ↓

Phase 6

&#x20;  ↓

Phase 7

```



Each major experiment has an associated JSON result file where applicable.



The original datasets must be obtained separately and placed in the appropriate local data directories. These files are intentionally excluded from version control.



\---



\# Documentation



A detailed project document is included in:



```text

QuantFormer\_Documentation.pdf

```



It provides the broader experimental methodology, implementation details, results, and analysis corresponding to the repository.



\---



\# Limitations



Several limitations should be considered when interpreting the results:



1\. \*\*Quantum simulation\*\*

&#x20;  The quantum circuit is simulated rather than executed on physical quantum hardware.



2\. \*\*Simulation cost\*\*

&#x20;  Quantum simulation can become computationally expensive as circuit size and workload increase.



3\. \*\*Dataset dependence\*\*

&#x20;  Performance varies substantially between datasets, particularly for more challenging class distributions.



4\. \*\*Limited parameter sweep\*\*

&#x20;  The reported experiments use a defined architecture and configuration rather than an exhaustive hyperparameter search.



5\. \*\*Benchmark-specific evaluation\*\*

&#x20;  Different datasets and experimental phases use different evaluation protocols; metrics should therefore be interpreted within their corresponding experimental setup.



6\. \*\*Dataset availability\*\*

&#x20;  The original HSI datasets are not redistributed in this repository.



\---



\# Research Outputs



The repository preserves more than final accuracy values. It includes:



\* Multi-seed benchmark results

\* Per-class performance

\* Confusion matrices

\* Classification maps

\* Ablation results

\* McNemar statistical tests

\* Effect-size analysis

\* t-SNE feature visualizations

\* Parameter-count comparisons

\* Inference-time measurements

\* Extracted model artifacts



This makes the repository useful not only for reproducing headline metrics but also for inspecting the behavior of the model across datasets and experimental conditions.



\---



\# Citation



If you use this implementation or experimental results in academic work, please cite the repository:



```bibtex

@software{anjum2026quantformer,

&#x20; author  = {Amama Anjum},

&#x20; title   = {QuantFormer: Quantum-Enhanced Transformer for Hyperspectral Image Classification},

&#x20; year    = {2026},

&#x20; version = {1.0},

&#x20; note    = {Research software repository}

}

```



\## Project Summary



\*\*QuantFormer investigates a compact hybrid quantum-classical Transformer for hyperspectral image classification through multi-dataset benchmarking, ablation analysis, statistical testing, and full-scene evaluation.\*\*



