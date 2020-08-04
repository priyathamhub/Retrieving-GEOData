# Retrieving-GEOData
In this Project we use the Google GeoCoding API to retrieve data and then use Google Maps to visualize the data.

using the Google geocoding API to clean up some user-entered geographic locations of university names and then placing the data on a Google Map.

You should install the SQLite browser to view and modify the databases.

Run the geoload.py to lookup all of the entries in where.data (including the new one) and produce the geodata.sqlite. Then run geodump.py to read the database and produce where.js. Then open where.html to visualize the map. 

In the first phase we take our input data in the file(where.data) and read it one line at a time, and retrieve the geocoded response and store it in a database (geodata.sqlite). Before we use the geocoding API, we simply check to see. 

You can re-start the process at any time by removing the file geodata.sqlite

Run the geoload.py program. This program will read the inputlines in where.data and for each line check to see if it is already in the database and if we don't have the data for the location, call the geocoding API to retrieve the data and store it in the database.

Here is a sample run after there is already some data in the
database:

Mac: python3 geoload.py
Win: geoload.py

Found in database  Northeastern University

Found in database  University of Hong Kong, Illinois Institute of Technology, Bradley University

Found in database  Technion

Found in database  Viswakarma Institute, Pune, India

Found in database  UMD

Found in database  Tufts University

Resolving Monash University
Retrieving http://py4e-data.dr-chuck.net/json?key=42&address=Monash+University
Retrieved 2063 characters {    "results" : [
{u'status': u'OK', u'results': ... }

Resolving Kokshetau Institute of Economics and Management
Retrieving http://py4e-data.dr-chuck.net/json?key=42&address=Kokshetau+Institute+of+Economics+and+Management
Retrieved 1749 characters {    "results" : [
{u'status': u'OK', u'results': ... }

The first five locations are already in the database and so they are skipped.  The program scans to the point where it finds un-retrieved locations and starts retrieving them.

The geoload.py can be stopped at any time, and there is a counter that you can use to limit the number of calls to the geocoding API for each run.

Once you have some data loaded into geodata.sqlite, you can visualize the data using the (geodump.py) program.  This program reads the database and writes tile file (where.js) with the location, latitude, and longitude in the form of executable JavaScript code.

A run of the geodump.py program is as follows:

Mac: python3 geodump.py
Win: geodump.py

Northeastern University, 360 Huntington Avenue, Boston, MA 02115, USA 42.3396998 -71.08975
Bradley University, 1501 West Bradley Avenue, Peoria, IL 61625, USA 40.6963857 -89.6160811
...
Technion, Viazman 87, Kesalsaba, 32000, Israel 32.7775 35.0216667
Monash University Clayton Campus, Wellington Road, Clayton VIC 3800, Australia -37.9152113 145.134682
Kokshetau, Kazakhstan 53.2833333 69.3833333
...
12 records written to where.js
Open where.html to view the data in a browser

The file (where.html) consists of HTML and JavaScript to visualize a Google Map.  It reads the most recent data in where.js to get the data to be visualized.  Here is the format of the where.js file:

myData = [
[42.3396998,-71.08975, 'Northeastern University, 360 Huntington Avenue, Boston, MA 02115, USA'],
[40.6963857,-89.6160811, 'Bradley University, 1501 West Bradley Avenue, Peoria, IL 61625, USA'],
[32.7775,35.0216667, 'Technion, Viazman 87, Kesalsaba, 32000, Israel'],
   ...
];

This is a JavaScript list of lists.  The syntax for JavaScript list constants is very similar to Python so the syntax should be familiar to you.

Simply open where.html in a browser to see the locations.  You can hover over each map pin to find the location that the gecoding API returned for the user-entered input.  If you cannot see any data when you open the where.html file, you might want to check the JavaScript or developer console for your browser.
