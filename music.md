### Récupération de tous les albums
- SELECT * FROM albums

### Récupérer tous les albums dont le titre contient "Great"
- SELECT * FROM albums WHERE Title LIKE 'Great%'

### Récupération du nombre total d'albums contenus dans la base (sans regarder les id bien sûr)
- SELECT COUNT(*) FROM albums

### Suppression de tous les albums dont le nom contient "music"
- SELECT * FROM albums WHERE Title NOT LIKE '%music%'

### Récupération de tous les albums écrits par AC/DC
- SELECT albums.AlbumId, artists.Name FROM albums INNER JOIN artists ON albums.ArtistId = artists.ArtistId WHERE Name ='AC/DC'

### Récupération de tous les titres des albums de AC/DC
- SELECT albums.AlbumId, albums.Title, artists.Name FROM albums INNER JOIN artists ON albums.ArtistId = artists.ArtistId WHERE Name ='AC/DC'

### Récupérer la liste des titres de l'album "Let There Be Rock"
- SELECT tracks.Name FROM tracks INNER JOIN albums ON albums.AlbumId = tracks.AlbumId WHERE tracks.AlbumId = 1

### Afficher le prix de cet album ainsi que sa durée totale
- SELECT SUM(UnitPrice) FROM (SELECT tracks.TrackId, tracks.Name, invoice_items.UnitPrice FROM tracks  INNER JOIN invoice_items ON invoice_items.TrackId = tracks.TrackId WHERE tracks.AlbumId = 1)

### Afficher le coût de l'intégralité de la discographie de "Deep Purple"
- SELECT SUM(UnitPrice), SUM(Milliseconds) FROM (SELECT tracks.TrackId, tracks.Name, tracks.Milliseconds, invoice_items.UnitPrice FROM tracks  INNER JOIN invoice_items ON invoice_items.TrackId = tracks.TrackId WHERE tracks.AlbumId = 1)
