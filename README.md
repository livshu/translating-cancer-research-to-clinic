# FTIR Spectroscopy + Machine Learning for Oral Lesion Classification

This repository contains the main code and supporting thesis for my MPhys project investigating whether Fourier Transform Infrared (FTIR) spectroscopy combined with machine learning methods can help distinguish benign and malignant oral epithelial lesions.

The project focuses on whether the functional IR band (2200–4000 cm⁻¹), which can be measured on standard **glass slides**, can provide clinically useful classification performance compared with the traditional fingerprint band (1000–1800 cm⁻¹) measured on CaF2 substrates. 


## What this repository includes

- `legacy_barney_scikit_functional60.ipynb`  
  Main notebook implementing the preprocessing, feature construction, masking, training, and evaluation pipeline for FTIR biopsy data using a **scikit-learn MLPClassifier**.

- `Translating Cancer Research to the Clinic.pdf`  
  Full thesis describing the physics background, preprocessing choices, model design, experimental setup, results, and discussion. 

## Method overview

The workflow used in this project is:

1. Load FTIR hyperspectral biopsy data and metadata
2. Build tissue and lesion masks
3. Extract spectral features from selected wavenumbers
4. Apply spectral normalisation and standard scaling
5. Train a **multi-layer perceptron (MLP)** on pixel-level spectra
6. Evaluate performance on unseen biopsy data using sensitivity and specificity.

The thesis compares several normalisation methods, including:
- global product normalisation
- local ratio normalisation
- local difference normalisation

The main reported architecture is a **scikit-learn MLPClassifier** with:
- 4 hidden layers
- 60 nodes per layer
- ReLU activations
- SGD optimisation
- L2 regularisation
- batch-based training on pixel spectra

## Key results

Using unseen biopsy data, the project found:

- **Fingerprint band:** 99% specificity and 89% sensitivity
- **Functional band:** 99% specificity and 77% sensitivity 

This showed that although the fingerprint band performs better, the functional band on standard glass slides still retains diagnostic value, with only a modest drop in sensitivity.  

The work also found that the model could, in some cases, highlight malignant regions beyond those manually marked by the histopathologist, with supporting evidence from k-means clustering. 

## Why this matters

A major barrier to FTIR adoption in pathology is the need for CaF2 slides, whereas standard histopathology workflows already use glass slides. Demonstrating useful classification performance on glass could make FTIR-based diagnostics more practical for real clinical settings. 


## Thesis

The accompanying thesis is included here as the main scientific reference for the project.
