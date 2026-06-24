# LionCity-Traffic-Intelligence-Jupyter-Notebooks
# Singapore Traffic Congestion — Research & Development

This repository contains the exploratory data analysis and model development work behind **LionCity Traffic Intelligence**, a Random Forest–based traffic congestion prediction system for Singapore.

🔗 **Live App:** [lioncity-traffic-intelligence.streamlit.app](https://lioncity-traffic-intelligence.streamlit.app/)
🔗 **Deployment Repo:** *(link to your app repo here)*

---

## 📁 Contents

### `EDA.ipynb`
Exploratory data analysis on a 2025 hourly Singapore traffic dataset covering temporal, environmental, and human-activity features.

- Data quality checks (missing values, types, duplicates) and an automated `ydata-profiling` report
- Hourly traffic and VC (volume-to-capacity) ratio trends, revealing a bimodal rush-hour pattern (7–9 AM, 17–19 PM)
- Weekday vs. weekend congestion comparison
- Seasonal (monthly) congestion trends, with December showing the highest average VC ratio
- Public holiday vs. normal day congestion distribution
- Impact of special events (concerts, festivals) on congestion
- Effect of rainfall intensity on average traffic speed
- Overall congestion level distribution

Each plot is paired with a written, quantified insight (e.g., a 57.86% traffic volume surge between 6–7 AM) rather than just a visual.

### `ML+SHAP.ipynb`
Model development and explainability work for the deployed application.

- Defines congestion levels (Low / Medium / High) from the VC ratio
- Trains a **Random Forest classifier** (85.5% accuracy) on 13 temporal, weather, and event-based features
- **Design decision:** vehicle speed (`avg_speed_kmh`) is deliberately excluded as a model input, since speed is a *consequence* of congestion, not a predictive cause — using it would make the prediction circular. Instead, speed ranges (25th–75th percentile per congestion class) are precomputed and shown alongside the prediction as supplementary context
- SHAP (TreeExplainer) analysis identifying tourist activity, hour of day, and school hours as the strongest drivers of HIGH congestion
- Exports the trained model, encoders, and SHAP background sample for use in the deployed Streamlit app

---

## 🛠️ Tech Stack
`Python` · `Pandas` · `NumPy` · `Scikit-learn` · `SHAP` · `Plotly` · `Seaborn` · `ydata-profiling`

---

## 📌 Note
These notebooks represent the research/development phase of the project. The production-ready app code, trained model artifacts, and deployment files live in a separate repository (linked above) to keep the deployable app clean and lightweight.
