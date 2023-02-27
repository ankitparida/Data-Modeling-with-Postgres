# Project: Data Modeling with Postgres

## Sparkify Postgres ETL

### Introduction

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

This project models user activity data for a music streaming app called Sparkify to optimize queries for understanding what songs users are listening to by creating a Postgres relational database and ETL pipeline to build up Fact and Dimension tables and insert data into new tables.

### ETL Pipeline

1. Create the required Dimension and Fact Tables for the first time in sparkifyDatabase.

   ***Command:  python3 create_tables.py***

2. There are two types of Dataset we are using here: Song Dataset and Log Dataset. Run the etl.py file which does the below steps:
    a. Process Song Files:  Process song dataset to insert record into songs and artists dimension table.
    b. Process Log Files: Process log file to insert record into time and users dimensio table and songplays fact table.

    ***Command: python3 etl.py***

3. The above processes can be interactively verified using the test.ipynb Jupyter Notebook.

### Important Files Description:

**1.test.ipynb:** displays the first few rows of each table for validation purpose.
**2.create_tables.py:** Used for dropping and creating the required tables.
**3.etl.ipynb:** reads and processes a single file from song_data and log_data and loads the data into the tables. This notebook contains detailed instructions on the ETL process for each of the tables.
**4.etl.py:** reads and processes files from song_data and log_data and loads them into your tables.
**sql_queries.py:** contains all the sql queries, and is imported into the last three files above.


### Schema for Song Play Analysis

#### Fact Table

**songplays** - records in log data associated with song plays i.e. records with page NextSong
Attributes:
    1. songplay_id
    2. start_time
    3. user_id
    4. level
    5. song_id
    6. artist_id
    7. session_id
    8. location
    9. user_agent

#### Dimension Tables

**users** - users in the app
    1. user_id
    2. first_name
    3. last_name
    4. gender
    5. level

**songs** - songs in music database
    1. song_id
    2. title
    3. artist_id
    4. year
    5. duration

**artists** - artists in music database
    1.artist_id
    2. name
    3. location
    4. latitude
    5. longitude
    
**time** - timestamps of records in songplays broken down into specific units
    1. start_time
    2. hour
    3. day
    4. week
    5. month
    6. year
    7. weekday
