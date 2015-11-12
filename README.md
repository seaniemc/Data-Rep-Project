#Data Representation Project
*Author: Sean McGrath*

#Playgrounds County Galway API*
##Introduction

This document will outline the design and documentation for the data set, Playgrounds County Galway. The data is available at <http://data.gov.ie> and comes in CSV files format, which can be easily convert into JSON files. The API can be used as part of a web application, which could create, update and delete information about playgrounds through out the county of Galway. 

##About the data

The data set comes in the form of CSV files which was downloaded from the http://data.gov.ie website. In order to make the data set more accessible, it will be converted into JSON. The data set has 16 fields and 63 entries. I will only use 14 fields, as there is 2 field which I feel there would be no benefit in using it. The field FID contains the identical data as the ID column and the PHOTO field contains links to external websites, but the links no longer work. There is also another slight duplication with the fields List_of_Eq, which lists the equipment in English and Liosta_Tre which lists the equipment in Gailge.

##Columns and Rows.

|Columns |Rows   |
|:------:|:-----:|
|"Id" | The id given to each playground |
|"Location_o"|Location of playground|
|"Area_" |Area of gounty eg: West Galway - Conamara|
|"Managed_By"| Eg: Roundstone Playground Committee|
|"Playground" | Eg: Roundstone Village, Connemara |
|"AGE_GROUP" |Age profile of users Eg: 0 to 16 years     |
|"List_of_Eq" |List of Equipment Eg: Climber and Slide, Climber with Rope|
|"Liosta_Tre" |List of Equipment in Irish Eg: Dreapadóir le Sleamhnán |
|"List_of_00" |Lists equipment suitable for small children Eg: Toddler swings |
| | |
| | |


```java

```
