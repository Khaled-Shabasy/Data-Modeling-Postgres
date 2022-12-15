# Project: Data modeling with Postgres

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Their data resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

The main role is to create a postgres database schema with tables designed to optimize queries on song play analysis and ETL pipeline for this analysis. 


## Database Schema Design

### This project uses the star schema as follows:

#### Fact Table

**songplays** - records in log data associated with song plays i.e. records with page NextSong
- songplay_id SERIAL PRIMARY KEY
- start_time timestamp NOT NULL
- user_id int NOT NULL
- level varchar
- song_id varchar
- artist_id varchar
- session_id int
- location varchar
- user_agent varchar

#### Dimension Tables

**users** - users in the app
- user_id int PRIMARY KEY
- first_name varchar
- last_name varchar
- gender varchar
- level varchar

**songs** - songs in music database
- song_id varchar PRIMARY KEY
- title varchar NOT NULL
- artist_id varchar
- year int NOT NULL
- duration numeric NOT NULL

**artists** - artists in music database
- artist_id varchar PRIMARY KEY
- name varchar NOT NULL
- location varchar
- latitude double precision
- longitude double precision

**time** - timestamps of records in songplays broken down into specific units
- start_time timestamp PRIMARY KEY NOT NULL
- hour int
- day int
- week int
- month int
- year int
- weekday int

### Creating Sparkify Database and Tables

- Write `CREATE` and `DROP` statements in `sql_queries.py` to create each table and to drop each table if it exists.
- Run `create_tables.py` to create your database and tables.

## Database ETL Pipeline

- Use `etl.ipynb` notebook to develop ETL processes for each table.
- The data extracted from the JSON song files in`data/song_data` populate the **songs** and **artists** tables
- The data extracted from the JSON log files in`data/log_data` populate the **users** and **time** tables
- A `SELECT` query extracts `song_id` and `artis_id` from the **songs** and **artists** tables to join them with the rest of the log data to populate the **songplays** table.
- At the end of each table section, or at the end of the notebook, run `test.ipynb` to confirm that records were successfully inserted into each table.
- Use what you've completed in `etl.ipynb` to complete `etl.py`, where you'll process the entire datasets. Remember to run `create_tables.py` before running `etl.py` to reset your tables
- Run `test.ipynb` to confirm your records were successfully inserted into each table.



