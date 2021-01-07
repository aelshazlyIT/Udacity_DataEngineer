
# Data Modeling with Postgres

my first project in udicity nanodegree 


# Overview
In this project, you'll apply what you've learned on data modeling with Postgres and build an ETL pipeline using Python. To complete the project, you will need to define fact and dimension tables for a star schema for a particular analytic focus, and write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.


# Datasets:

## Song Dataset
this is json format file contains song metadata
Sample Record :
```
{
  "num_songs": 1,
  "artist_id": "ARJIE2Y1187B994AB7",
  "artist_latitude": null,
  "artist_longitude": null,
  "artist_location": "",
  "artist_name": "Line Renaud",
  "song_id": "SOUPIRU12A6D4FA1E1",
  "title": "Der Kleine Dompfaff",
  "duration": 152.92036,
  "year": 0
}
```

## Log Dataset
this is json format file contains song logdata
Sample Record :
```
{
  "artist": "Pavement",
  "auth": "Logged In",
  "firstName": "Sylvie",
  "gender": "F",
  "itemInSession": 0,
  "lastName": "Cruz",
  "length": 99.16036,
  "level": "free",
  "location": "Washington-Arlington-Alexandria, DC-VA-MD-WV",
  "method": "PUT",
  "page": "NextSong",
  "registration": 1540266185796.0,
  "sessionId": 345,
  "song": "Mercy:The Laundromat",
  "status": 200,
  "ts": 1541990258796,
  "userAgent": "\"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_4) AppleWebKit/537.77.4 (KHTML, like Gecko) Version/7.0.5 Safari/537.77.4\"",
  "userId": "10"
}
```


# Schema


## Fact Table 
**songplays** - records in log data associated with song plays i.e. records with page `NextSong`

```
songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

1    2018-11-29 00:00:57.796000    73    paid    -    -    954    Tampa-St. Petersburg-Clearwater, FL
```

## Dimension Tables
**users**  - users in the app
```
user_id, first_name, last_name, gender, level

79    James    Martin    M    free

```
**songs**  - songs in music database
```
song_id, title, artist_id, year, duration

SOFFKZS12AB017F194    A Higher Place (Album Version)    ARBEBBY1187B9B43DB    1994    236.17261
```
**artists**  - artists in music database
```
artist_id, name, location, latitude, longitude

ARNNKDK1187B98BBD5    Jinx    Zagreb Croatia    45.80726    15.9676
```
**time**  - timestamps of records in  **songplays**  broken down into specific units
```
start_time, hour, day, week, month, year, weekday

2018-11-29 00:01:30.796000    0    29    48    11    2018    3
```





# to run the code:


create_tables.py: Clean previous schema and creates tables.
sql_queries.py: All queries used in the ETL pipeline.
etl.py: Read JSON logs and JSON metadata and load the data into generated tables.


