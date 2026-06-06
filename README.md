Dubai Metro SQL Intermediate Analysis Showcase
This document contains a series of business-driven questions answered using intermediate SQL techniques applied to the metro_stations.csv dataset.  


CHALLENGE 1:
* Write a query from scratch that selects the station_name and to_burj_khalifa_km. Add a new conditional column called proximity_status that follows these rules:  
If it is less than 10 km from Burj Khalifa, label it 'Very Close'.
If it is between 10 km and 25 km (inclusive), label it 'Commuter Distance'.
Anything greater than 25 km should be labeled 'Far Out'.*/

SQL:
SELECT  station_name, to_burj_khalifa_km,
    CASE 
        WHEN to_burj_khalifa_km < 10 THEN 'Very Close'
        WHEN to_burj_khalifa_km BETWEEN 10 AND 25 THEN 'Commuter Distance'
        ELSE 'Far Out'
    END AS proximity_status
FROM metro_stations;

RESULT:
"UAE Exchange"	"32.11"	"Far Out"
"Energy"	"30.29"	"Far Out"
"Ibn Battuta"	"23.16"	"Commuter Distance"
"Jebel Ali"	"25.65"	"Far Out"
"Danube"	"25.04"	"Far Out"
"UAE Pavilion"	"23.75"	"Commuter Distance"
"MRT-1"	"22.92"	"Commuter Distance"
"Discovery Gardens"	"21.52"	"Commuter Distance"
"Al Furjan"	"22.59"	"Commuter Distance"
"Jumeirah Golf Estates"	"21.75"	"Commuter Distance"
"Dubai Investment Park"	"25.36"	"Far Out"
"Expo 2020"	"29.6"	"Far Out"
"Dubai Internet City"	"14.68"	"Commuter Distance"
"Mashreq Bank"	"15.34"	"Commuter Distance"
"Mall of the Emirates"	"11.49"	"Commuter Distance"
"Sharaf DG"	"13.19"	"Commuter Distance"
"Noor Bank"	"9.92"	"Very Close"
"First Abu Dhabi Bank"	"7.99"	"Very Close"
"Business Bay"	"1.56"	"Very Close"
"Burj Khalifa/Dubai Mall"	"0.32"	"Very Close"
"Financial Centre"	"1.6"	"Very Close"
"Emirates Towers"	"2.4"	"Very Close"
"World Trade Centre"	"3.27"	"Very Close"
"Max"	"4.66"	"Very Close"
"Al Jafiliya"	"4.07"	"Very Close"
"BurJuman"	"6.82"	"Very Close"
"ADCB"	"7.38"	"Very Close"
"Al Karama"	"7.15"	"Very Close"
"Union"	"8.69"	"Very Close"
"Baniyas Square"	"8.5"	"Very Close"
"Salah Al Din"	"10.13"	"Commuter Distance"
"Abu Hail"	"11.55"	"Commuter Distance"
"Abu Baker Al Siddique"	"10.82"	"Commuter Distance"
"Al Qiyadah"	"12.64"	"Commuter Distance"
"Stadium"	"14.34"	"Commuter Distance"
"Al Nahda"	"14.3"	"Commuter Distance"
"Centrepoint"	"13.85"	"Commuter Distance"
"Etisalat"	"11.92"	"Commuter Distance"
"Al Qusais"	"13.72"	"Commuter Distance"
"Dubai Airport Free Zone"	"12.73"	"Commuter Distance"
"Al Nahda (G)"	"14.52"	"Commuter Distance"
"Stadium (G)"	"14.22"	"Commuter Distance"
"Al Qiyadah (G)"	"12.6"	"Commuter Distance"
"Abu Baker Al Siddique (G)"	"10.82"	"Commuter Distance"
"Salah Al Din (G)"	"10.28"	"Commuter Distance"
"Union (G)"	"8.69"	"Very Close"
"Al Ras"	"7.8"	"Very Close"
"Palm Deira"	"7.37"	"Very Close"
"Baniyas Square (G)"	"8.5"	"Very Close"
"Al Ghubaiba"	"6.96"	"Very Close"
"BurJuman (G)"	"6.82"	"Very Close"
"Oud Metha"	"5.74"	"Very Close"
"Dubai Healthcare City"	"5.89"	"Very Close"
"Al Jadaf"	"6.7"	"Very Close"
"Creek"	"8.2"	"Very Close".



CHALLENGE 2:
/*Management wants to look at the size of the different metro networks in your data.  
Write a query that shows each metro line and the total number of stations belonging to that line.Only display lines that have more than 15 stations total.  */

SQL:
SELECT line, COUNT(*)
FROM metro_stations
 GROUP BY line 
HAVING COUNT(*) >15

RESULT:
"Red"	"37"
"Green"	"18"


CHALLENGE 3:
/*Write a query from scratch that selects the station_name from the metro_stations table, forces all the station names into all uppercase letters while renaming that specific column header AS clean_name, and filters the rows using a WHERE clause combined with LIKE so that the output only displays stations where the name starts with the letter 'A'.*/

SQL:
SELECT UPPER(station_name) AS clean_name
FROM metro_stations
WHERE station_name LIKE 'A%'

RESULT:
"AL FURJAN"
"AL JAFILIYA"
"ADCB"
"AL KARAMA"
"ABU HAIL"
"ABU BAKER AL SIDDIQUE"
"AL QIYADAH"
"AL NAHDA"
"AL QUSAIS"
"AL NAHDA (G)"
"AL QIYADAH (G)"
"ABU BAKER AL SIDDIQUE (G)"
"AL RAS"
"AL GHUBAIBA"
"AL JADAF"



