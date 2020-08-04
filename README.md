# Retrieving-GEOData
In this Project we use the Google GeoCoding API to retrieve data and then use Google Maps to visualize the data.

using the Google geocoding API to clean up some user-entered geographic locations of university names and then placing the data on a Google Map.

You should install the SQLite browser or VS CODE to view and modify the databases.

Run the geoload.py to lookup all of the entries in where.data (including the new one) and produce the geodata.sqlite. 

![geodump py](https://user-images.githubusercontent.com/58246016/89280098-c4cc8480-d665-11ea-8ccb-1580a0342a5b.png)

Then run geodump.py to read the database and produce where.js. 


Then open where.html to visualize the map. 
