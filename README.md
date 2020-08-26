# apache_cassandra_music_db
Modeling a Spotify-like music database using NoSQL within a Python wrapper.

## Background
This project creates an ETL pipeline that makes song data available for the analytics team at the startup Sparkify to understand what songs users are listening to.
Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app. This project creates an Apache Cassandra database with tables designed to optimize queries on song play analysis.

## Key Concepts
1. Model the data tables keeping in mind the queries you need to run.

## Data
1. **Event Dataset** - Each file is in csv format and is partitioned by date.
For example, here are filepaths to two files in this dataset:

`event_data/2018-11-08-events.csv`
`event_data/2018-11-09-events.csv`

Below is an example of a single event file:

`{"num_songs": 1, "artist_id":..........................}`



