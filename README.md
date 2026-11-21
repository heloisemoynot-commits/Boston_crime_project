# Crime in Boston (2015-2018)

Final project for the *Programming for Data Science* course.

## Team
- FirstName FamilyName (team head)
- FirstName FamilyName
- FirstName FamilyName

## What we did
We used the KDD process on the Boston Police Department incident reports (June 2015 to September 2018) to build a small
visualization prototype. The data has a temporal dimension (date and hour), a spatial one (latitude, longitude, district)
and an analytical one (offense type, seriousness, shooting).

The notebook answers four questions:
1. **Grouping**: which offenses are the most frequent, and in which districts?
2. **Frequent pattern mining**: which offense / district / time of day / weekday combinations show up together? (Apriori, association rules)
3. **Temporal**: how many incidents can we expect per day in the next 6 months? (Prophet forecast, checked with the MAE on the last 90 days)
4. **Spatial**: where are the hotspots for larceny? (DBSCAN with haversine distance)

Bonus: we join daily weather data from NOAA to see if temperature is linked to the number of incidents.

All results are gathered in a Dash dashboard. A static export is in `familyNameLeader_dashboard.html`.

## Data
- Main dataset: [Crimes in Boston (Kaggle)](https://www.kaggle.com/datasets/AnalyzeBoston/crimes-in-boston), file `crime.csv`
- External dataset: NOAA daily summaries for Boston Logan airport (station USW00014739), saved as `boston_weather.csv`

Put both files in the same folder as the notebook.

## Repository content
| File | Description |
|---|---|
| `familyNameLeader_notebook.ipynb` | the notebook (all code is in functions, called from the main block at the end) |
| `familyNameLeader_dashboard.html` | static export of the dashboard |
| `requirements.txt` | Python libraries needed |
| `crime.csv`, `boston_weather.csv` | the data |

## How to run
```bash
pip install -r requirements.txt
jupyter notebook familyNameLeader_notebook.ipynb
```
Then run all cells. The dashboard opens inside the notebook (set `RUN_DASH = False` in the main block to skip it).
