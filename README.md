# CNC_cost_estimation_assignment
# CNC Cost Estimation – Data Science Intern Assignment

## 📌 Objective

This project predicts machining cost and cycle time using scraped CNC part data enriched with geometric and manufacturing features.

---

## 🔍 Approach Summary

1. **Scraping**:
   - Used Selenium to scrape 49 listings from Alibaba for real CNC machined parts.
   - Extracted: Title, Material, Estimated Price.

2. **Data Cleaning**:
   - Cleaned price formats and removed duplicates.
   - Saved as `alibaba_cleaned_base.csv`.

3. **Feature Engineering**:
   - Enriched each row with:
     - Randomized `Length_mm`, `Width_mm`, `Height_mm`
     - Computed `Volume_mm3`, `Feature_Count`, `Cycle_Time_min`
     - Added `Cost_per_mm3` and `CycleTime_per_Feature`

4. **Visualization**:
   - Analyzed trends: Cost vs Volume, Cycle Time vs Feature Count, Correlation Heatmap
   - Output stored as .png plots

5. **Modeling**:
   - Trained both **Random Forest** and **Linear Regression** on the enriched dataset.
   - Target: `Cycle_Time_min`

---

## 📊 Summary of Results

| Model | MAE | RMSE |
|-------|-----|------|
| Random Forest | 3.52 | 4.64 |
| Linear Regression | ~ | ~ (excluded due to feature leakage and corrected later) |

- **Random Forest** outperformed Linear Regression
- **Volume** and **Feature Count** were top predictors

---

## 💡 Key Insights

- Feature count (machining complexity) and part volume have strong predictive power.
- `Cost_per_mm3` helped detect parts that are expensive per unit size, hinting at material or complexity cost.
- The hybrid approach of real scraping + synthetic enrichment is effective for modeling when full data isn’t available.

---

## 🧠 Reflection

- Manufacturing data often lacks structure — combining scraping with logical feature generation was essential.
- Real-world model performance would improve significantly with CAD-based features and material processing properties.

---

## 📂 Files

- `CNC_Cost_Estimation.ipynb` – full workflow (scraping, cleaning, features, modeling)
- `.csv` files – raw, cleaned, and enriched datasets
- `.png` – visualizations
- Scripts – used to modularize cleaning and modeling logic

