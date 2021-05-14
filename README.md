# Names
 TDI Winter 2021 capstone project, "Hey I know that name!"

Note: I would not recommend opening the name_pronunciation_storage folder in a file browser, there are about 100,000 files in it. 

Project outline:
1. Business objective:
This project is intended to provide users with information about what names "fit" in a given era, for a given age demographic. This is useful for both advertising and creating believable period media. In the near future, this project will be updated to include an interactive site. It is currently limited to US names, at the national level. 
2. Data ingestion:
The name and actuarial data used in this project come from the US Social Security Administration, with pronunciation data from the Datamuse web API. The data have been pulled through a combination of manual and automated processes, as described in the "Names_preprocessing" notebook. Manually-collected data is currently included in the notebook.
3. Visualizations:
There are a large number of reference visualizations throughout the project, but the two user-facing visualizations are a word cloud (with custom color to indicate age) and a sparkline-like display of the most relevant names, which includes information on specificity, weight, and the time course of the name's popularity. 
4. Machine learning/Interactive website:
The project relies in part on machine learning techniques for name trend recognition. A more common subset of names is clustered using affinity propagation, based on both spelling and pronunciation similarity. The time trend of each cluster is then projected using ARIMA via the pmdarima package, and combined with a model of individual name time courses based on cluster trends, using RidgeCV from the scikit-learn package. This generates an estimate of each name's future popularity over the next five years.

Other notes:

Order of operations, fresh:
  0. Copy actuarial files ("life_" files) from actuarial data
  1. Run "Names_calculate_reduced", takes half an hour to prepare files for core visualizations.
      - For pronunciation data, takes most of a day to re-scrape the Datamuse data.
  2. Run "Names_visualize_reduced", loads saved datafiles

Order of operations, with existing files:
  0. Run "Names_visualize_reduced"