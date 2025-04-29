📚 GEOTWEETS-STOICISM-ANALYSIS

🚀 PROJECT OVERVIEW
This repository contains the complete pipeline and visualizations for analyzing the evolution of Stoicism-related discourse on Twitter using geotagged tweets collected between 2010 and 2023.
We leverage spatial and temporal analysis to track the presence and intensity of Stoic concepts and philosophical trends over time.

🎯 OBJECTIVES
- Identify and track the frequency of Stoicism-related keywords in geolocated tweets.
- Visualize temporal trends and thematic shifts across thirteen years.
- Analyze the geographic distribution of Stoicism discourse.
- Provide structured outputs (datasets, graphs, cluster summaries) for academic research.

🗂️ DATA SOURCES
- Raw Data: Private geotagged Twitter datasets.
- Data Period: 2010–2023.
- Structure: TSV files with fields including:
message_id, date, text, tags, tweet_lang, place, latitude, longitude, etc.
📌 Note: The original geotagged dataset is private and not publicly available due to data usage agreements.

- KEYWORD FILTERING
The analysis uses two levels of keyword matching to ensure precision and coverage:

🔍 Wildcard Keywords (prefix matching):
altrui*, aristot*, cosmop*, epictet*, epicur*, eudaimon*, hedon*, philosoph*, plato*, pythago*, socrat*, stioc*, stoic*

🎯 Exact Keywords (exact word matching):
amorfati, aurelius, chrysippus, cicero, cleanthes, commongood, dichotomyofcontrol,
diogenes, hadot, humandignity, humanworth, jordanpeterson, mattis, mementomori,
moralinjury, moralaction, moralprogress, moralpurpose, musoniusrufus, nussbaum,
peripatetic, pigliucci, ryanholiday, seneca, stockdale, timferriss, zeno

This two-step strategy ensures comprehensive yet precise filtering of Stoic discourse without introducing unrelated topics.

🛠️ PIPELINE OVERVIEW
The workflow follows a structured process:
1. Data Loading 📥 — Load geotagged tweets for each year.
2. Keyword Filtering 🧹 — Apply curated wildcard and exact keyword filters.
3. Frequency Calculation 📊 — Aggregate yearly keyword frequencies.
4. Visualization 🎨 — Generate trendline graphs over time.
5. Spatial Clustering 📍 — Detect geospatial clusters of Stoicism tweets.
6. Country-Level Summary 🌍 — Aggregate tweets per country based on geolocation.
7. Output Generation 📄 — Export CSV datasets and visual outputs.

Full implementation is available in the notebook Geotweets_Stoicism_Analysis_v6.ipynb.

- OUTPUTS
- keyword_frequencies_by_year.csv: Yearly keyword frequency dataset.
- stoicism_cluster_summary.csv: Spatial clustering of Stoicism tweets.
- tweets_by_country.csv: Summary of tweets per country (based on latitude/longitude).
- Trend graphs (4 PNG images) illustrating keyword trends from 2010 to 2023.
- Jupyter Notebook with full reproducible code and methodology.

- CLUSTERING ANALYSIS (SPATIAL DISTRIBUTION)
An optional spatial analysis was performed using the HDBSCAN clustering algorithm (haversine distance) on geolocated tweets.
- Minimum cluster size: 30 points
- Minimum samples per cluster: 10
- Noise points: excluded
- Total detected clusters: 10,552
The cluster centroids and tweet counts are saved in:
- stoicism_cluster_summary.csv
This enables further analysis of the geographic density and spatial patterns of Stoicism discourse.


- COUNTRY-LEVEL ANALYSIS (GEOLOCATION-BASED)
Using latitude and longitude, each tweet was reverse-geocoded to a country code, generating a country-level summary of Stoicism activity.
- Tweets matched using offline reverse geocoding for speed and security.
- Output saved in:
tweets_by_country.csv

Using latitude and longitude coordinates, each Stoicism-related tweet was reverse-geocoded to a country code, generating a detailed country-level summary.
Tweets were processed using offline reverse geocoding (reverse_geocoder) to ensure speed, scalability, and data security.
Batch processing (10,000 points per batch) was implemented to handle over 1.6 million coordinates without memory overload.
Country names were mapped using the pycountry library for standardized naming.
Outputs:
tweets_by_country.csv: Contains the number of tweets per country along with the ISO country code.
top10_countries_stoicism.png: Visualization of the Top 10 countries with the most Stoicism-related tweets.
- Top 10 countries are automatically displayed when running the pipeline.
  

### 🗓️ Yearly Tweet Count Summary

A total of **1,670,801** Stoicism-related tweets were extracted between 2010 and 2023. The table below shows the distribution by year:

| Year | Tweets   |
|:----:|---------:|
| 2011 |        1 |
| 2012 |    1,275 |
| 2013 |  154,557 |
| 2014 |  301,105 |
| 2015 |  147,553 |
| 2016 |   41,050 |
| 2017 |   54,719 |
| 2018 |  115,224 |
| 2019 |  235,449 |
| 2020 |  206,053 |
| 2021 |  153,282 |
| 2022 |  214,783 |
| 2023 |   45,750 |

📄 CSV file available at: `tweet_counts_by_year.csv`



- HOW TO RUN
1. Clone the repository:
git clone https://github.com/cga-harvard/Geotweets-Stoicism-analysis.git
2. Open the Geotweets_Stoicism_Analysis_v5.ipynb notebook.
3. Adjust data paths if necessary.
4. Execute all cells to reproduce the analysis.


- Requirements:
Python 3.11+
pandas
matplotlib
seaborn
hdbscan
reverse_geocoder
pycountry
Optimized for high-performance computing environments (HPC).



- AUTHORS
  - Rafael Albuquerque — Federal University of Rio Grande do Sul (UFRGS) | Visiting Fellow at Harvard CGA
  - Devika Jain — Harvard Center for Geographic Analysis (CGA)



- ACKNOWLEDGMENTS
This research was conducted at the Harvard Center for Geographic Analysis (CGA).
Special thanks to the CGA research team and affiliated collaborators for their support.
