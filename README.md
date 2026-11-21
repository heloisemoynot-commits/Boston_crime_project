# Crime in Boston (2015-2018)

Final project for the *Programming for Data Science* course.

Repository: https://github.com/heloisemoynot-commits/Boston_crime_project

## Team
- Héloïse MOYNOT (team head)
- Estelle HU
- Alice QUENTREC
- Tashaly SOBNACK

## What we did
We used the KDD process on the Boston Police Department incident reports (June 2015 to September 2018) to build a small
visualization prototype. The data has a temporal dimension (date and hour), a spatial one (latitude, longitude, district)
and an analytical one (offense type, seriousness, shooting).

The notebook answers four questions:
1. **Grouping**: which offenses are the most frequent, and in which districts?
2. **Frequent pattern mining**: which offense / district / time of day / weekday combinations show up together? (Apriori, association rules)
3. **Temporal**: how many incidents can we expect per day in the next 6 months? (Prophet forecast, checked with the MAE on the last 90 days)
4. **Spatial**: where are the hotspots for larceny? (DBSCAN with haversine distance)

Bonus : we join daily weather data to see if temperature is linked to the number of incidents. Without the file, this part is skipped.

All results are gathered in a Dash dashboard. Static exports are in `MOYNOT_dashboard.html` (interactive, open it in a
browser) and `MOYNOT_dashboard.pdf`.

## Data
- Main dataset: [Crimes in Boston (Kaggle)](https://www.kaggle.com/datasets/AnalyzeBoston/crimes-in-boston), file `crime.csv`.
  It is too big for GitHub (58 MB), so the repository has the zip from Kaggle: unzip it to get `crime.csv`.
- External dataset (optional): NOAA daily summaries for Boston Logan airport (station USW00014739), saved as `boston_weather.csv`
  ([download link](https://www.ncei.noaa.gov/access/services/data/v1?dataset=daily-summaries&stations=USW00014739&startDate=2015-06-01&endDate=2018-09-30&dataTypes=TMAX,TMIN,PRCP&units=metric&format=csv))

Put the csv files in the same folder as the notebook.

## Repository content
| File | Description |
|---|---|
| `MOYNOT_notebook.ipynb` | the notebook (all code is in functions, called from the main block at the end) |
| `MOYNOT_dashboard.html` | static export of the dashboard (open it in Chrome / Edge / Firefox) |
| `MOYNOT_dashboard.pdf` | PDF version of the dashboard |
| `requirements.txt` | Python libraries needed |
| `crimes-in-boston.zip` | the data (contains `crime.csv`) |

## How to run
```bash
pip install -r requirements.txt
jupyter notebook MOYNOT_notebook.ipynb
```
Then run all cells. The dashboard opens inside the notebook (set `RUN_DASH = False` in the main block to skip it).
