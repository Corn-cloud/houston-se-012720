# Intro to SQL

1. Install the SQLite Browser if you haven't already [here](http://sqlitebrowser.org/)
2. Open the SQLite Browser and click 'File -> Open DataBase'
3. Choose the `chinook.db` file from this repo. This database is open source and maintained by Microsoft (SQL is no fun if you don't have any data)
4. Click the tab that says 'Execute SQL'. Type SQL queries in the box above. Press the play button. See the results of that query in the box below

## Challenges

1. Write the SQL to return all of the rows in the artists table?

```SQL
SELECT * FROM artists
```

2. Write the SQL to select the artist with the name "Black Sabbath"

```SQL
SELECT * FROM artists WHERE name = "Black Sabbath"
SELECT * FROM artists WHERE name LIKE "% Eyed %"
SELECT * FROM artists WHERE name LIKE "%Bla%"
```

3. Write the SQL to create a table named 'fans' with an autoincrementing ID that's a primary key and a name field of type text

```sql
CREATE TABLE fans_new(id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT)
```

4. Write the SQL to alter the fans table to have a artist_id column type integer?

```sql
ALTER TABLE fans_new ADD COLUMN artist_id INTEGER
```

5. Write the SQL to add yourself as a fan of the Black Eyed Peas? ArtistId **169**

```sql
INSERT INTO fans_new (name, artist_id) VALUES ("Vidhi", 169)
```

6. How would you update your name in the fans table to be your new name? Use Ruby file.

```sql
UPDATE fans_new SET name = "Vidhi sharma" WHERE id =10
```

7. Write the SQL to return fans that are not fans of the black eyed peas.

```sql
SELECT * FROM fans_new WHERE NOT artist_id = 169
SELECT * FROM fans_new WHERE artist_id != 169
```

8. Write the SQL to display an artists name next to their album title

```sql
SELECT artists.name, albums.title 
FROM artists JOIN albums 
WHERE artists.id = albums.artist_id
```

9. Write the SQL to display artist name, album name and number of tracks on that album

```sql
SELECT artists.name, albums.title, COUNT(tracks.name) 
FROM artists
JOIN albums
ON artists.id = albums.artist_id
JOIN tracks
ON albums.id = tracks.album_id
GROUP BY albums.id
```

10. Write the SQL to return the name of all of the artists in the 'Pop' Genre

```sql
SELECT DISTINCT artists.name FROM artists
JOIN albums
ON artists.id = albums.artist_id
JOIN tracks
ON albums.id = tracks.album_id
JOIN genres
ON tracks.genre_id = genres.id
WHERE genres.Name = 'Pop';
```

