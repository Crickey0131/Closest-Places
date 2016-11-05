postgres=# Create Table Points5 (
postgres(# name VARCHAR(15),
postgres(# loc geometry);

postgres=# Insert into Points5 values ('Tuscany', ST_GeomFromText('POINT(-118.282 34.017)', 4326));
postgres=# Insert into Points5 values ('Science Center', ST_GeomFromText('POINT(-118.286 34.016)', 4326));
postgres=# Insert into Points5 values ('Coliseum', ST_GeomFromText('POINT(-118.288 34.015)', 4326));
postgres=# Insert into Points5 values ('Galon Center', ST_GeomFromText('POINT(-118.280 34.021)', 4326));
postgres=# Insert into Points5 values ('Starbucks', ST_GeomFromText('POINT(-118.282 34.019)', 4326));
postgres=# Insert into Points5 values ('LVL', ST_GeomFromText('POINT(-118.283 34.022)', 4326));
postgres=# Insert into Points5 values ('Bookstore', ST_GeomFromText('POINT(-118.286 34.021)', 4326));
postgres=# Insert into Points5 values ('SSL', ST_GeomFromText('POINT(-118.289 34.02)', 4326));
postgres=# Insert into Points5 values ('Lyon Center', ST_GeomFromText('POINT(-118.288 34.025)', 4326));

postgres=# SELECT ST_AsText(ST_ConvexHull(ST_Collect(loc))) FROM Points5;

postgres=# SELECT a.name From Points5 a, Points5 b WHERE a.name <> 'Tuscany' AND b.name = 'Tuscany' ORDER BY ST_Distance(a.loc, b.loc) LIMIT 3;
