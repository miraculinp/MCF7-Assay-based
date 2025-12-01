# MCF-7 Cell Line Assay-Based Anticancer Activity Prediction  
![GitHub](https://img.shields.io/github/stars/miraculinp/MCF7-Assay-based?style=social)  
![Python](https://img.shields.io/badge/Python-3.12-blue.svg)  
![RDKit](https://img.shields.io/badge/RDKit-2025+-green)  
![License](https://img.shields.io/badge/License-MIT-yellowgreen.svg)  

https://github.com/miraculinp/MCF7-Assay-based

A high-performance QSAR modeling pipeline for predicting anticancer activity (pIC₅₀) against the **MCF-7 human breast adenocarcinoma cell line** using large-scale assay data from PubChem/ChEMBL.


## Project Highlights

- **Dataset**: >15,000 diverse small molecules with experimentally measured IC₅₀ values on MCF-7 cells  
- **Target**: Regression of pIC₅₀ = –log₁₀(IC₅₀ in M)  
- **Feature Set** (~1,400 features):  
  - Morgan fingerprints (radius=2, 1024 bits)  
  - MACCS keys (167 bits)  
  - Comprehensive RDKit 2D descriptors (MW, logP, TPSA, H-bond donors/acceptors, etc.)  
- **Models Trained & Tuned**:  
  Random Forest • XGBoost • LightGBM • ElasticNet • SVR • MLP  
- **Final Model**: **Stacked Ensemble** (Ridge meta-learner) → **Best performer**  
- **Interpretability**: Full SHAP analysis on top-performing model (XGBoost + ensemble)  
- **Reproducibility**: Fixed seeds, timestamped model/prediction saving, publication-ready plots


```

git clone https://github.com/miraculinp/MCF7-Assay-based.git
cd MCF7-Assay-based

# Recommended: Use Google Colab (one-click RDKit install included)
# Or locally:
pip install rdkit molvs tqdm pandas numpy scikit-learn xgboost lightgbm shap matplotlib seaborn

Then open and run the notebook:  
`MCF7_QSAR_Stacked_Ensemble.ipynb`

The notebook will:
1. Load and clean the MCF-7 dataset  
2. Standardize SMILES and remove duplicates/outliers  
3. Generate molecular descriptors & fingerprints  
4. Train + tune 7 base models  
5. Build stacked ensemble with 5-fold OOF predictions  
6. Evaluate with detailed metrics & beautiful plots  
7. Perform SHAP interpretability on the best model  
8. Save everything with a timestamp:
   - Trained models (`.pkl`)
   - Scaler
   - Full predictions + metadata (`.csv`)
   - Results summary (`.json`)
   - High-resolution plots (parity, SHAP, residuals)

## Key Outputs (Example)

- `shap_summary.png` – Global feature importance for anticancer activity  
- `parity_plot_test.png` – Predicted vs Experimental pIC₅₀  
- `predictions_with_metadata_20251201_123456.csv` – Full test set with all model predictions  
- Top SHAP features typically include:  
  - Molecular weight  
  - Aromatic proportion  
  - Number of rotatable bonds  
  - Presence of specific nitrogen/sulfur patterns (common in known chemotherapeutics)

## Applications

- Virtual screening of compound libraries against breast cancer cell lines  
- Lead optimization guidance via SHAP feature contributions  
- Understanding molecular determinants of MCF-7 cytotoxicity

## Contributing

Contributions are very welcome! Feel free to:
- Submit new datasets
- Add new models or fingerprint types
- Improve visualization or interpretability sections

Just fork → make changes → open a Pull Request.

## License

MIT License – free to use, modify, and distribute.

## Contact & Citation

**Author**: Olapade Miracle  
**Email**: olapademiracleo@gmail.com  





Star the repo if you find it useful in your drug discovery journey!  

Let's accelerate anticancer drug discovery together!
