# apache_cassandra_music_db
Modeling a Spotify-like music database using Apache Cassandra and NoSQL within a Python wrapper.

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

The .csv files have the following fields; most are self-explanatory:
- artist
- auth: How the user gained authorization
- firstName
- gender
- itemInSession
- lastName
- length
- level
- location
- method
- page
- registration
- sessionId
- song
- status
- ts: timestamp
- userId

## Project File Structure
1. `music_cassandra_db.ipynb` main project file. 
2. `event_data` contains the .csv files
3. `data_snippet_view.jpg` contains a snapshot of the csv data files extracted in Part 1 of `music_cassandra_db.ipynb`.
4. `README.md` provides discussion on the project.
5. `Annotated_Project_Notes.ipynb` an annotated version of `music_cassandra_db.ipynb` with more in-depth instructions.

## Steps to Follow
### Part I Pre-Process the files.
1. Run the cells to extract relevant values from the collection of .csv files
2. Verify that no rows were lost

### Part II Run Apache Cassandra code to create tables.
1. Create a cluster, connect to the cluster, create a keyspace, and set the keyspace.
2. Create tables that are specifically tailored to the three queries of interest.
3. Confirm that the queries return the correct values.

## Issues faced and solutions
### Part I.
#### Issue: The .csv files did not combine in Part I, and only return 12 observations instead of 6,821 observations.
    # Join the file path and roots with the subdirectories using glob
    # Did not work: file_path_list = glob.glob(os.path.join(root,'*'))
    # Solution: Hard code the file path because above original code threw an error.
    # file_path_list = glob.glob('/home/workspace/event_data/*.csv')
