#County Galway Playgrounds API

##Data Representation Project

####Author: Sean McGrath

##Introduction

This document will outline the design and documentation for the data set, Playgrounds County Galway. The data is available at <http://data.gov.ie> and comes in CSV files format, which can be easily convert into JSON files. The API can be used as part of a web application, which could create, update and delete information about playgrounds through out the county of Galway. 

##About the data

The data set comes in the form of CSV files which was downloaded from the http://data.gov.ie website. In order to make the data set more accessible, it will be converted into JSON. The data set has 16 fields and 63 entries. I will only use 14 fields, as there is 2 field which I feel there would be no benefit in using. The field FID, contains identical data to that of the ID column and the PHOTO field contains links to external websites, but the links no longer work. There is also another slight duplication with the fields List_of_Eq, which lists the equipment in English and Liosta_Tre which lists the equipment in Gailge.

##Columns and Rows.

|Columns |Rows   |
|:------:|:-----:|
|X |The X position on the map Eg: -1104192 |
|Y |The Y position on the map Eg: 7056858|
|"Id" | The Id given to each playground |
|"Location_o"|Location of playground|
|"Area_" |Area of county Eg: West Galway - Connemara|
|"Managed_By"| Eg: Roundstone Playground Committee|
|"Playground" | Eg: Roundstone Village, Connemara |
|"AGE_GROUP" |Age profile of users Eg: 0 to 16 years     |
|"List_of_Eq" |List of Equipment Eg: Climber and Slide, Climber with Rope|
|"Liosta_Tre" |List of Equipment in Irish Eg: Dreapadóir le Sleamhnán |
|"List_of_00" |Lists equipment suitable for small children Eg: Toddler swings |
|"PUBLIC_TOI"|Yes/No |
|"OPENING_HO"|Eg: Daylight Hours |
|"PARKING"| Yes/No |

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

##Url Design

In the case where someone wants to acess the data and get a read only copy back, the GET method will be used. The data will be returned in JSON format.  
http://www.galwayplaygrounds.ie/playgrounds/all  
This will return all the parks in the data set in a JSON Array.

With the HTTP protocol we can use paramatorised quries, to get back more specific results in our data.  
http://www.galwayplaygrounds.ie/playgrounds/parking/[Yes/No]   
http://www.galwayplaygrounds.ie/playgrounds/parking/yes  
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

````











