# Sparkify Postgres ETL Project

Project submission for the Udacity Data Engineering Nanodegree.

This project consists of putting into practice the following concepts:
- Data modeling with Postgres using Star Schema
- ETL pipeline using Python

## Project Summary

In this project, we are doing data modeling with Postgres and building an ETL pipeline using Python so the analytics team at Sparkify can easily get data of which songs the users are listeing to in the app.

### Data

- **Song datasets**: all json files are nested in subdirectories under */data/song_data*. Sample Data:

```
{"num_songs": 1, "artist_id": "ARD7TVE1187B99BFB1", "artist_latitude": null, "artist_longitude": null, "artist_location": "California - LA", "artist_name": "Casual", "song_id": "SOMZWCG12A8C13C480", "title": "I Didn't Mean To", "duration": 218.93179, "year": 0}
```

- **Log datasets**: all json files are nested in subdirectories under */data/log_data*. Sample Data:

```
{"artist":"The Killers","auth":"Logged In","firstName":"Jayden","gender":"M","itemInSession":32,"lastName":"Graves","length":246.80444,"level":"paid","location":"Marinette, WI-MI","method":"PUT","page":"NextSong","registration":1540664184796.0,"sessionId":594,"song":"Read My Mind","status":200,"ts":1542672042796,"userAgent":"\"Mozilla\/5.0 (Windows NT 6.3; WOW64) AppleWebKit\/537.36 (KHTML, like Gecko) Chrome\/36.0.1985.143 Safari\/537.36\"","userId":"25"}
```
## Database Schema (Star)

This Star Schema consists of one fact table *songplays* and four dimension tables: *songs*, *artists*, *users* and *time*

## Project structure

Files used on the project:
1. **data** directory where all json data resides.
2. **sql_queries.py** contains all your SQL queries.
3. **create_tables.py** Creates tables required for this project. Execute this file to reset tables to a clean state each time before running the ETL scripts.
4. **test.ipynb** Test script to fetch data.
5. **etl.ipynb** ETL script which extract, transform and load the data to the songplays table. 
6. **etl.py** ETL script which extract, transform and load the data to the songplays table. 
7. **README.md**.

## Data Processing and Quality Checks

Data is extracted from two types of JSON source files: song data from the [Million Song Dataset](https://labrosa.ee.columbia.edu/millionsong/) and songplay data from user logs. The JSON files are read into pandas dataframes, processed and uploaded into the database using psycopg2. 

Steps taken to clean the data and reduce the size of the database by removing data not needed for this analysis: 
* Songplays are identified by filtering for actions initiated from the 'NextSong' page. 
* Timestamps are converted from UNIX time to datetime format.

## How to Use

1. Execute create_tables.py from terminal (`python create_tables.py`) to set up the database and tables.
2. Execute etl.py (`python etl.py`) from terminal to process and load data into the database.
3. Launch test.ipynb notebook to run validation and example queries.

## Author 
Pratik Shah
