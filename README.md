# Flight Delays Analysis & Prediction Project

This project analyzes and predicts flight delays using the 2015 Flight Delays and Cancellations dataset from Kaggle. The dataset includes scheduled passenger flights in the U.S. with airline, flight number, departure and arrival times, delay durations, and cancellation/diversion info. The project applies modern Big Data techniques, ETL, visualization, KPI analysis, and predictive modeling.

---

## Folder Structure

- **`raw_data/`**  
  Contains uncleaned XLSX files directly downloaded from Kaggle.

- **`cleanedData/`**  
  Contains the cleaned Power BI dataset used for dashboard creation and analysis.

- **`Dashboard/`**  
  Power BI file showcasing interactive dashboards with KPIs, trends, and visualizations.

- **`combinedNotebook/`**  
  Contains the main Jupyter Notebook where ETL, KPIs, visualizations, and predictive models were executed.

- **`reports/`**  
  Contains the predictive model report and a Plotly HTML file of interactive graphs.

---

## Notebook Overview (`combinedNotebook`)

1. **Load Data**  
   Load raw flight datasets and set file paths for preprocessing.

2. **Robust Merges & Type Fixes**  
   - Ensured airport/airline codes are strings.  
   - Merged airline names and airport metadata with distinct prefixes.

3. **Time Preprocessing**  
   - Extracted hours and minutes from HHMM format.  
   - Added cyclical encoding (sin/cos) for time features.

4. **Outlier Capping**  
   - Created `_CAPPED` columns for departure delays (1st/99th percentile) to reduce outlier effects.

5. **Delay Buckets & Feature Engineering**  
   - Delay buckets: On-time ≤5, Minor 6–30, Major >30 minutes.  
   - Added `ROUTE` (ORIGIN→DEST), `DATE` from YEAR/MONTH/DAY, and `DEP_HOUR_BIN`.

6. **KPI Builder Helper**  
   - Computed consistent KPIs (mean, median, 95th percentile, #flights, on-time%).  
   - `build_kpi()` used to generate tables by hour, airline, and route.

7. **Exploratory Visualizations**  
   - Average departure delay by hour, monthly delay trends.  
   - Top airlines and airports by delay.

8. **Advanced Visualizations**  
   - Heatmaps, distributions, month×hour charts, route maps, airport geo-maps, airline dashboards.

9. **Predictive Modeling**  
   - Logistic Regression to predict delayed (>5 min) vs on-time flights.  
   - Imputation, categorical encoding, confusion matrix, ROC curves.  
   - Separate model for severe delays (>60 min).

10. **Rolling Metrics & Report Exports**  
    - Daily on-time % and 7-day rolling averages.  
    - Exported KPIs to Excel and interactive Plotly HTML.

11. **Conclusions & Next Steps**  
    - Early morning flights and off-peak months have fewer delays.  
    - Late afternoon and high-traffic months have more delays.  
    - Airline and airport performance varies; insights help optimize travel.  
    - Future work could include additional predictive factors like weather and route trends.

---

## Tools & Libraries Used

- Python: `pandas`, `numpy`, `pyspark`, `plotly`, `scikit-learn`  
- Power BI for dashboards and reporting  
- Jupyter Notebook for ETL, visualizations, and modeling  

---

This project integrates Big Data processing, interactive visualization, KPI analysis, and machine learning to provide actionable insights into U.S. flight delays.
