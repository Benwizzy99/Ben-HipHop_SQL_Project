# HipHop_SQL_Project
## A Data Analyst project on Hiphop artist using SQL

This Data Analyst project was designed to help us know the best performing HipHop artist over the years.
# SQL Project: Hiphop Artists

### Artist Table
![Artist Table]()<img width="1690" height="766" alt="Screenshot 2025-08-29 171016" src="https://github.com/user-attachments/assets/f741496d-7280-4c1e-8036-fed4fe352234" />


### Albums Table<img width="1693" height="770" alt="Screenshot 2025-08-29 171039" src="https://github.com/user-attachments/assets/3d722eac-2a05-46e1-a3d4-1ac351e8c744" />

![Albums Table](screenshots/albums_table.png)



### Tools

- SQL

### Data cleaning/Preparation
Data loading and inspection
Data Cleaning and formatting.

### Exploratory Data Analysis (EDA)
- Who are the best hiphop artist
- Everything Concerning this artist,from their albums to their networths etc

  ### Result
  - We Discovered the top 10 best poerfoming artist
  - We also discovered the best Recore labels in terms of numbers
    
### Ten queries from the Artist and Album table
#### -- 1. List all artist names and countries

SELECT artist_name, country FROM hiphop_artists;

#### -- 2. Artists from USA with net worth > 100

SELECT artist_name, net_worth_million
FROM hiphop_artists
WHERE country = 'USA' AND net_worth_million > 100;

#### -- 3. All artists ordered by streams descending

SELECT artist_name, streams_billion
FROM hiphop_artists
ORDER BY streams_billion DESC;

#### -- 4. Average net worth of all artists

SELECT AVG(net_worth_million) AS avg_networth FROM hiphop_artists;

#### -- 5. Total albums per continent

SELECT continent, SUM(albums) AS total_albums
FROM hiphop_artists
GROUP BY continent;

#### -- 6. Continents with more than 30 albums

SELECT continent, SUM(albums) AS total_albums
FROM hiphop_artists
GROUP BY continent
HAVING total_albums > 30;

#### -- 7. List all albums with artist names

SELECT a.artist_name, al.album_name, al.release_year
FROM hiphop_albums al
JOIN hiphop_artists a ON al.artist_id = a.artist_id;

#### -- 8. Albums released after 2018 with artist country

SELECT a.artist_name, a.country, al.album_name, al.release_year
FROM hiphop_albums al
JOIN hiphop_artists a ON al.artist_id = a.artist_id
WHERE al.release_year > 2018;

#### -- 9. Total album sales per artist, ordered highest first

SELECT a.artist_name, SUM(al.sales_million) AS total_sales
FROM hiphop_albums al
JOIN hiphop_artists a ON al.artist_id = a.artist_id
GROUP BY a.artist_name
ORDER BY total_sales DESC;

#### -- 10. Artists with >1 album and total streams > 5 billion

SELECT a.artist_name, COUNT(al.album_id) AS album_count, SUM(al.streams_billion) AS total_streams
FROM hiphop_albums al
JOIN hiphop_artists a ON al.artist_id = a.artist_id
GROUP BY a.artist_name
HAVING album_count > 1 AND total_streams > 5;

🙏 Thank you 👋
