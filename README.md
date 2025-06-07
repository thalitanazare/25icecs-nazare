# Chaotic Jerk-Based Reservoir Computing for Anomaly Detection

This repository contains the source code and data used in the experiments reported in the paper:

**"A Chaotic Jerk-Based Reservoir Computing Approach for DoS Attack Detection"**  
(*ICECS 2025 submission*)  

The project investigates the use of a continuous-time chaotic Jerk system as the reservoir in a Reservoir Computing (RC) framework for detecting anomalies in network traffic. Two case studies are presented:

- Case 01: Detection of Denial-of-Service (DoS) attacks in the NSL-KDD dataset.
- Case 02: Classification of anomalies during a real-world DDoS event using the RIPE DDoS2020 dataset.

## Repository Structure
```
├── Case 01/
│   ├── KDDTrain+.txt
│   ├── KDDTest+.txt
│   ├── main5.ipynb
│   ├── pyESN.py
├── Case 02/
│   ├── rrc14main.ipynb
│   ├── fig_compare_article.svg
│   ├── fig_compare_article.pdf
│   ├── updates.*.{txt,gz}
├── README.md
├── 25ICECS_RC_NN.pdf
```

## Case 01: NSL-KDD DoS Attack Detection

This case study implements a binary classification task to distinguish between normal and DoS-labelled traffic samples from the NSL-KDD dataset.

### Files

- `KDDTrain+.txt` and `KDDTest+.txt`: Preprocessed NSL-KDD data files containing training and testing samples. Only "normal" and "DoS" classes are retained.
- `main5.ipynb`: Jupyter notebook implementing the full pipeline:
  - Data loading and preprocessing
  - Dimensionality reduction (PCA)
  - Construction of temporal input windows
  - Reservoir Computing with:
    - A chaotic Jerk system-based reservoir (implemented in notebook)
    - A baseline Echo State Network (ESN), using `pyESN.py`
  - Feature extraction and classification using a Random Forest
  - Evaluation metrics: Accuracy, F-score, ROC curve
- `pyESN.py`: Implementation of a canonical Echo State Network (ESN) class, used for comparison with the Jerk-based model.  
  The ESN is implemented as a discrete-time reservoir with tunable parameters such as spectral radius and sparsity:contentReference[oaicite:2]{index=2}.

## Case 02: RIPE DDoS2020 Anomaly Detection

This case study evaluates the Jerk-based reservoir on a real-world dataset capturing a distributed denial-of-service (DDoS) event targeting Amazon Web Services (AWS).

### Files

- `rrc14main.ipynb`: Jupyter notebook implementing the experiment:
  - Loading and preprocessing of RIPE DDoS2020 BGP updates
  - Construction of temporal input windows
  - Simulation of the Jerk system as a reservoir
  - Feature extraction and classification using a Random Forest
  - Comparative evaluation with ESN baselines reported in prior literature:Reference [3] from the article.
- `fig_compare_article.pdf` and `fig_compare_article.svg`: Figures generated for the article, comparing the performance of the proposed Jerk-based model and ESN baselines.
- `updates.*.{txt,gz}`: Raw RIPE Routing Information Service (RIPE RIS) BGP update files used as input data.

## Dependencies

The notebooks rely on the following Python packages:

- `numpy`
- `scikit-learn`
- `matplotlib`
- `pandas`
- `scipy`

Ensure that all required packages are installed prior to running the notebooks.

## Reproducibility

All experiments reported in the article can be reproduced using the code and data provided in this repository:

- **Case 01** reproduces the results of Table I and Figure 3, 4 in the paper.
- **Case 02** reproduces the results of Figure 5.

## License

This repository is intended for academic use. If you use this work, please cite the corresponding paper.

## Contact

Thalita Nazaré  
Hamilton Institute  
Maynooth University, Ireland  
thalita.nazare.2023@mumail.ie
