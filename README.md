# Movies-ETL

This repository creates an ETL pipeline for movie data extracted from kaggle and wikipedia.

The ETL_clean_kaggle_data.ipynb file extracts and cleans the kaggle data.

The ETL_clean_wiki_movies.ipynb file extracts and cleans the wikipedia movie data.

The ETL_create_database.ipynb file combines the functions of the previous two files and merges the dataframes as well as ratings data.  The script then loads the data into PostgreSQL.

To use the functions from these files as dependencies, insert the following at the top of your script:

```
from ETL_create_database import clean_movie, extract_transform_load
```

The extract_transform_load function will call the clean_movie function defined earlier in that script, so both are necessary.

## Functions

- extract_transform_load

This function takes three arguments: the Wikipedia data, the Kaggle metadata, and the MovieLens ratings data (from Kaggle).  It then uses the clean_movie function to remove superfluous titles from the raw wikipedia data as well as clean up the column names to make them more manageable.  The extract_transform_load function then combs through the various columns and cleans the data by converting to the most useful data types, formatting the data uniformly, and dropping unnecessary columns.

Once the data is clean, the data is loaded into Pandas dataframes and merged.  The function then sends the data to PostgreSQL tables for further analysis.