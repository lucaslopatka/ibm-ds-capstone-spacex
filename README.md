# SpaceX Falcon 9 – First-Stage Landing Prediction

Capstone project for the **IBM Data Science Professional Certificate**.
Goal: predict whether a Falcon 9 first stage will land successfully, using public launch data (2010–2020).

## Repository contents

| File | What it does |
|---|---|
| `Module_10_1.ipynb` | Web scraping of the Wikipedia launch tables + data wrangling of the course dataset (creates the `Class` label) |
| `Module_10_2.ipynb` | Exploratory data analysis with SQL (SQLite) and Seaborn charts, plus feature engineering |
| `Module_10_3.ipynb` | Interactive map with Folium (sites, outcomes, distances) and the Plotly Dash dashboard (site dropdown, payload slider, pie and scatter charts) |
| `Module_10_4.ipynb` | Machine learning: Logistic Regression, SVM, Decision Tree and KNN tuned with GridSearchCV |
| `dataset_part_2.csv`, `dataset_part_3.csv` | Datasets produced along the way (optional) |
| `Report Data Science Project - LL.pdf` | Final presentation |

## Method in short
1. **Collect:** Wikipedia scraping (BeautifulSoup). The SpaceX REST API was attempted but was unavailable, so the course's `dataset_part_1.csv` (loaded by URL in `Module_10_1.ipynb`) is used for wrangling.
2. **Wrangle:** clean the data, group landing outcomes, create `Class` (1 = landed, 0 = did not).
3. **Explore:** 10 SQL queries and Seaborn charts (payload, site, orbit, year).
4. **Map and dashboard:** Folium markers, clusters and distance lines; Dash app with callbacks (both in `Module_10_3.ipynb`).
5. **Model:** one-hot encoding, 80/20 split, standard scaling, GridSearchCV (10-fold).

## Key results
- 90 Falcon 9 launches; 66.7% landed successfully.
- Yearly success rate rose from 0% (2013) to roughly 85–90% (2019–2020).
- Logistic Regression, SVM and KNN reach **83.3%** test accuracy; Decision Tree reaches 77.8%.
- No model misses a real landing, but all over-predict success (small test set: 18 rows).

## How to run
```bash
pip install pandas numpy requests beautifulsoup4 seaborn matplotlib scikit-learn folium dash plotly
jupyter notebook   # open the notebooks in order: 10_1 → 10_2 → 10_3 → 10_4
# In Module_10_3.ipynb, run the Dash cell and open http://127.0.0.1:8050
```

## Notes
- The Folium maps and the Dash app are interactive, so GitHub does not render them. Screenshots are in the presentation.
- The SpaceX API is community-run and can be slow or unavailable; the notebooks also use static copies of the data provided by the course.
