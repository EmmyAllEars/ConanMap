# Collaborative Conan Map
Aimee Jarboe

https://twitter.com/ProbablyAimee

![Conan Map example](https://camo.githubusercontent.com/a93fd7e582ae1a1746aec6b71ebce6f30424b6b6/687474703a2f2f692e696d6775722e636f6d2f656361346b63442e6a7067 "Conan Map example")

++++++++++++++++++++++++++++++++

The Collaborative Conan Map is intended to give clans a way to share ingame locations. Using Google Maps API and a zoomable version of the ingame map, players can place map markers by right-clicking the map. Markers can be dragged before they're saved, and deleted after. 

Custom icons for the different types of markers are: Camp (campfire icon), Enemy (Darfari mask), NPC Friendly (Leather Journal), Base (Stygian flag), Resource (mining pick), and Landmark (torch). To change the icons on your map, upload desired graphic with the name scheme `"pin_" + type + ".png"` to `/images/icons/` (example: the Camp type icon is `pin_camp.png`). See current icons if you need help with naming.  

++++++++++++++++++++++++++++++++

Requirements:

 * Server with LAMP stack
 * make sure php-dom is installed and enabled
 * enabled Google Maps API key ("Get a Key" button at https://developers.google.com/maps/documentation/embed/)


1) Create table in mysql database:

 
 ```
 CREATE TABLE IF NOT EXISTS 'markers' (
   'id' int(11) NOT NULL AUTO_INCREMENT,
   'name' varchar(60) NOT NULL,
   'address' varchar(80) NOT NULL,
   'lat' float(10,6) NOT NULL,
   'lng' float(10,6) NOT NULL,
   'type' varchar(30) NOT NULL,
   PRIMARY KEY ('id')
 ) ENGINE=MyISAM DEFAULT CHARSET=latin1 AUTO_INCREMENT=1 ;
 ```


2) open index.php and replace following values:

 * "YOUR_API_KEY" with your Google Maps API key in URL on line 6
 * "---YOUR DOMAIN HERE---" in icon references with your domain.

3) open map_process.php and fill in the following values:

```
 // database settings 
 $db_username = '';
 $db_password = '';
 $db_name = 'mysql';
 $db_host = 'localhost';
 ```

4) Upload contents to server.

++++++++++++++++++++++++++++

Troubleshooting:

* If results "Could not create marker!", check all columns in db table were created.
 
