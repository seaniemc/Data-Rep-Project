#County Galway Playgrounds API

##Data Representation Project

####Author: Sean McGrath

##Introduction

This document will outline the design and documentation for the data set, Playgrounds County Galway. The data is available at <http://data.gov.ie> and comes in CSV files format, which can be easily convert into JSON files. The API can be used as part of a web application, which could create, update and delete information about playgrounds through out the county of Galway. 

##About the data

The data set comes in the form of CSV files which was downloaded from the http://data.gov.ie website. In order to make the data set more accessible, it will be converted into JSON. The data set has 16 fields and 63 entries. I will only use 14 fields, as there is 2 field which I feel there would be no benefit in using. The field FID, contains identical data to that of the ID column and the PHOTO field contains links to external websites, but the links no longer work. There is also another slight duplication with the fields List_of_Eq, which lists the equipment in English and Liosta_Tre which lists the equipment in Gailge.

##Columns and Rows.


##Sample of Data in JSON Format.

Below you will see a sample of the data from the CSV file represented in JSON form. Take note of the headings and the correspondent data associated with each heading.

```json
 {
    "X":-1104192,
    "Y":7056858,
    "ID":1,
    "Location_o":"Roundstone (Cloch na Ron)",
    "Area_":"West Galway - Conamara",
    "Managed_By":"Roundstone Playground Committee",
    "Playground":"Roundstone Village, Connemara",
    "AGE_GROUP":"0 to 16 Years",
    "List_of_Eq":"Climber and Slide, Climber with Rope, Flat Swings, Cradle Swings, Crazy Goose, Springer, Spring SeeSaw, Platform & Slide",
    "Liosta_Tre":"Dreapadóir le Sleamhnán, Luascán Cothrom,  Luascán Cliabháin , Lingeadan, Maide Corrach, srl.",
    "List_of_00":"Toddler swings",
    "PUBLIC_TOI":"NO",
    "OPENING_HO":"Daylight Hours",
    "PARKING":"YES"
  },
```
##Accessing The Data Set Through The API
Accessing the data set is done through the HTTP prtocol, using the GET, PUT and POST method. I will not allow the use of the DELETE Method as the likely Hood of a Playground been deleted is slim.

##URL Design

In the case where someone wants to acess the data and get a read only copy back, the GET method will be used. The data will be returned in JSON format.  
http://www.galwayplaygrounds.ie/en/playgrounds/all  
This will return all the parks in the data set in a JSON Array.

With the HTTP protocol we can use paramatorised quries, to get back more specific results from our data. In the URL below the /parking segment details the particular field which you want use as a paramtuer in the result of the query. The /yes segement details the value for which the result should return.  

http://www.galwayplaygrounds.ie/en/playgrounds/parking/[Yes/No]   
http://www.galwayplaygrounds.ie/en/playgrounds/parking/yes   

When this HTTP request is ran it will return a result set of all the parks with parking.  
Below is an example of the JSON returned by the HTTP request.

```json
{
    "X":-1115105,
    "Y":7074415,
    "ID":29,
    "Location_o":"Clifden (An Clochán)",
    "Area_":"West Galway - Conamara",
    "Managed_By":"Clifden Playground",
    "Playground":"Beach Road, Clifden",
    "AGE_GROUP":"0-12 Years",
    "List_of_Eq":"Boat, Three Way Spring Rocker, Spinning Bowl, Super Nova, Crazy Goose Rocker, Crazy Hen,     Swings, Basket Swings, Swings, Cable Runway",
    "Liosta_Tre":"Bád, Luascaire Sprionga,  Babhla Rothalithe, Luascáin, Ciseán Luascadh, Rúíidchosán Cábhla",
    "List_of_00":"None specified.",
    "PUBLIC_TOI":"No",
    "OPENING_HO":"Daylight Hours",
    "PARKING":"YES"
  },

```
http://www.galwayplaygrounds.ie/en/playgrounds/area/[Name of area]   
http://www.galwayplaygrounds.ie/en/playgrounds/area/north-galway-tuam  
When this HTTP request is ran it will return a result set of all the parks from the Area Noth Galway -Tuam.  
Below is an example of the JSON returned by the HTTP request.

```json
{
    "X":-946083,
    "Y":7070276,
    "ID":13,
    "Location_o":"Mountbellew (An Creagán)",
    "Area_":"North Galway - Tuam",
    "Managed_By":"Mountbellew Community Playground",
    "Playground":"GAA Pitch, Tuam Road",
    "AGE_GROUP":"0 to 12 years",
    "List_of_Eq":"Cableway, Mobilus, Junior Multiplay Unit, Seesaw, Embankment Tube Slide, Cradle Swings, Flat Seat Swings, Basket Swing, Jeep Spring Unit, Spring Seesaw, Toddler Multiplay Unit, Pedal Roundabout,  4 Seat Springer and Car Springer",
    "Liosta_Tre":"Rúidchosán Cábla, Mobilus, Aonad Ilspraoi Sóisearach, Maide Corrach, Sleamhnán, Luascáin, Luascán Cothrom, Ciseán Luascadh, Aonad Ilspraoi Lapadáin, Timpeallán, srl.",
    "List_of_00":"Swinging Basket & Play Jeep",
    "PUBLIC_TOI":"No",
    "OPENING_HO":"09.00 to 8.30 (Summer) 09.00 to 5.00 (Winter)",
    "PARKING":"YES"
  },

```
####Using Filters To Query Data 

We can use filters to return the exact data which is needed. We first set the filter using a field (i.e "List_of_Eq") from the data set. Then set the parameter (i.e Seesaw).  
http://galwayplaygrounds.ie/en/playgrounds/?[filter]=[parameter]  
http://galwayplaygrounds.ie/en/playgrounds/?list_of_eq=seesaw  
This will return JSON formated objects, which have a Seesaw listed in the "List_of_Eq" section. 

####Update With The PUT Method
We can use the PUT method to update the data set.
http://www.galwayplaygrounds.ie/playgrounds/update?objectid=[id]&field=[field]&values=[value]  
http://www.galwayplaygrounds.ie/playgrounds/update?objectid=[50]&field=[PUBLIC_TOI]&values=[YES]  

This will change value of the field "PUBLIC_TOI" from "NO" to "YES", in the object with the ID of 50.

#####Add With The POST Method
We can use the POST method to add a new entry to the data set.  
PUT /en/playgrounds.html HTTP/1.1  
HOST: www.galwayplaygrounds.ie  
Connection: Keep-Alive  
Content-type: text/html  
x=-987451&y=741258&id=64&Location_o=Renvyle&Area_=WestGalway-Conamara............etc









