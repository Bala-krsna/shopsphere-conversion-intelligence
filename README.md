# ShopSphere Conversion Intelligence

**Capstone Project — E-Commerce Analytics Domain**

An end-to-end data science project analyzing session-level customer behavior on the ShopSphere e-commerce marketplace to identify the drivers of purchase conversion, evaluate marketing channel effectiveness, and test three research hypotheses using classification modeling, SHAP interpretability, and autoencoder-based anomaly detection.

## Business Problem

ShopSphere has substantially increased digital marketing spend across search, social, affiliate, display, and email channels. Despite strong traffic growth, leadership faces rising Customer Acquisition Cost (CAC) and declining Return on Ad Spend (ROAS), with many visitors engaging on the platform without converting. This project investigates which customer, behavioral, and campaign factors actually drive conversion, using session-level data.

## Key Findings

- **Channel and demographics do not predict conversion.** campaign_type, traffic_source, customer_segment, gender, city, device_type, month, and day of week all show under 1.6 percentage points of variation in conversion rate — statistically flat.
- **In-session behavioral engagement drives conversion.** cart_additions, wishlist_additions, and discount_viewed account for the overwhelming majority of predictive signal (49.1% of total SHAP importance concentrated in just 5 of 51 features).
- **ad_clicks and email_clicks show ~zero correlation with conversion** — directly relevant to the business complaint that campaigns generate clicks without conversions.
- **Data quality caveat:** the dataset's 83.8% conversion rate (vs. a typical 1–5% e-commerce baseline), combined with four further structural anomalies discovered during analysis, suggests this dataset may not represent fully organic customer behavior. This is documented transparently in the final report (Section 10) and should be validated against live ShopSphere data before any recommendation is used commercially.

## Methodology

1. Data understanding, cleaning, and documented assumption logging
2. Exploratory data analysis, including a dedicated leakage-risk investigation into `cart_additions`
3. Feature engineering, including a dual-pipeline design (Model A: full features, Model B: pre-cart features only) to test for target leakage
4. Model development: Random Forest vs. Logistic Regression baseline
5. SHAP-based interpretability analysis
6. Autoencoder-based anomaly detection (unsupervised)
7. Business recommendations grounded in evidence, with an honest limitations log

## Repository Structure

```
├── README.md
├── requirements.txt
├── notebooks/
│   └── ShopSphere_Capstone_Notebook.ipynb   # Full analysis, cell-by-cell with explanations
├── reports/
│   ├── ShopSphere_Capstone_Report.docx      # Full technical report
│   └── ShopSphere_PreSubmission_Document.docx
└── outputs/
    ├── cart_additions_chart.png             # Key EDA visualization
    └── workflow_diagram_v3.png              # Proposed analytical workflow
```

**Note on data:** the raw dataset (`ShopSphere_Conversion_Intelligence.csv`) is not included in this repository. To run the notebook, place the CSV in the same folder as the notebook before executing.

## Tech Stack

- **Data handling:** pandas, numpy
- **Modeling:** scikit-learn (Random Forest, Logistic Regression)
- **Interpretability:** SHAP
- **Deep learning:** TensorFlow/Keras (autoencoder)
- **Visualization:** matplotlib
- **Statistics:** scipy

## How to Run

1. Install dependencies: `pip install -r requirements.txt`
2. Place `ShopSphere_Conversion_Intelligence.csv` in the `notebooks/` folder
3. Open `notebooks/ShopSphere_Capstone_Notebook.ipynb` in Jupyter
4. Run cells sequentially from top to bottom

## Author

[Balakrishna / Praveen / Surendra] — [AIAGET B2]
