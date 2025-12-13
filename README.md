# Search for Neutrinoless Double-Beta Decay (NLDBD)

**DSC 291 Physics Final Project**  
**Authors:** Zijie Feng, Joshua Chuang, Shiyu Li  
**Institution:** UC San Diego

---

## Overview

This project implements a complete statistical analysis pipeline for searching for **Neutrinoless Double-Beta Decay (NLDBD)** using simulated data inspired by the **Majorana Demonstrator** experiment.

---

## Repository Structure

```
dsc291physicsfinalproject/
│
├── DSC291_Physics_Final_Project_Code.ipynb   # Main analysis notebook
├── README.md                             # This file
├── DetectorA.csv                         # Calibration source (signal-like)
├── DetectorB.csv                         # Calibration source (background-like)
├── DetectorC.csv                         # Background detector
└── DetectorTarget.csv                    # Target dataset for NLDBD search
```
---

## Usage

1. Open `DSC291_Physics_Final_Project_Code.ipynb` in Jupyter
2. Run all cells sequentially (Cell → Run All)
3. Examine generated plots and fit results
4. Modify parameters to explore different analysis choices

### Running Individual Steps

The notebook is organized into 8 main steps:

```python
# Step 1: Load data and visualize energy spectra
loaded_data, energy_bins = load_and_plot_spectra()

# Step 2: Calculate True Positive Rate (TPR)
calculate_and_plot_tpr(loaded_data['Detector A'])

# Step 3: Calculate False Positive Rate (FPR)
calculate_and_plot_fpr(loaded_data['Detector B'])

# Step 4: Generate NLDBD signal PDF
nldbd_pdf = generate_nldbd_pdf(energy_bins)

# Step 5: Generate fitting PDFs with optimal cut
fitting_inputs = generate_fitting_pdfs(loaded_data, energy_bins, nldbd_pdf, cut_threshold=0.15)

# Step 6: Perform frequentist fit
best_fit_params = perform_corrected_fit(fitting_inputs, loaded_data, cut_threshold=0.15)

# Step 7: Calculate 90% CL upper limit
upper_limit = step_7_calculate_upper_limit(fitting_inputs, loaded_data, best_fit_params)

# Step 8: Calculate experimental sensitivity
sensitivity = step_8_calculate_sensitivity(fitting_inputs, loaded_data, best_fit_params)
```

## Key Results

### Best-Fit Parameters

| Parameter | Fitted Value | Expected Value |
|-----------|--------------|----------------|
| **θ_A** | 1190.5 | ~1350 
| **θ_B** | 752.5 | ~770 |
| **θ_C** | 300.6 | Unknown | N/A |
| **θ_NLDBD** | **20.94** | Unknown |

### Statistical Results

| Metric | Value | 
|--------|-------|
| **Observed Upper Limit (90% CL)** | 37.95 events |
| **Expected Sensitivity** | 10.75 events |
| **Ratio (Obs/Exp)** | **3.5×** |
| **Best-Fit Signal** | 20.94 events |
