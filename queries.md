# Type of Triangle

Source: https://www.hackerrank.com/challenges/what-type-of-triangle/problem?isFullScreen=true

Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

Equilateral: It's a triangle with 3 sides of equal length.
Isosceles: It's a triangle with 2 sides of equal length.
Scalene: It's a triangle with 3 sides of differing lengths.
Not A Triangle: The given values of A, B, and C don't form a triangle.

Input Format

The TRIANGLES table is described as follows:

***Input Format***  
  
The TRIANGLES table is described as follows:  

| Column | Type    |
| -------| --------|
| A      | Itneger |
| B      | Integer |
| C      | Integer |
  
***Solution***   

```
SELECT
  CASE 
    WHEN A + B <= C or A + C <= B or B + C <= A THEN 'Not A Triangle'
    WHEN A = B and B = C THEN 'Equilateral'
    WHEN A = B or A = C or B = C THEN 'Isosceles'
    WHEN A <> B and B <> C THEN 'Scalene'
  END
FROM TRIANGLES;
```
  
# Weather Observation Station 18

Source: https://www.hackerrank.com/challenges/weather-observation-station-18/problem?isFullScreen=true  	

Consider P<sub>1</sub>(a,b) and P<sub>2</sub>(c,d) to be two points on a 2D plane.

* a happens to equal the minimum value in Northern Latitude (LAT_N in STATION).
* b happens to equal the minimum value in Western Longitude (LONG_W in STATION).
* c happens to equal the maximum value in Northern Latitude (LAT_N in STATION).
* d happens to equal the maximum value in Western Longitude (LONG_W in STATION).
Query the Manhattan Distance between points  P<sub>1</sub> and  P<sub>2</sub> and round it to a scale of 4 decimal places.

***Input Format***

The STATION table is described as follows:

| Field  | Type         |
| -------| -------------|
| ID     | NUMBER       |
| CITY   | VARCHAR2(21) |
| STATE  | VARCHAR2(2)  |
| LAT_N  | NUMBER       |
| LONG_W | NUMBER       |


***Solution***

```
SELECT ABS(ROUND(((MIN(lat_n)-MAX(lat_n))+(MIN(long_w)-MAX(long_w))), 4)) FROM station;
```

# Average Population of Each Continent

Source: https://www.hackerrank.com/challenges/average-population-of-each-continent/problem?isFullScreen=true

Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

***Input Format***

The CITY and COUNTRY tables are described as follows:

CITY

| Field       | Type         |
| ------------| -------------|
| ID          | NUMBER       |
| NAME        | VARCHAR2(17) |
| COUNTRYCODE | VARCHAR2(3)  |
| DISTRICT    | VARCHAR2(20) |
| POPULATION  | NUMBER       |

COUNTRY

| Field          | Type         |
| ---------------| -------------|
| CODE           | VARCHAR2(3)  |
| NAME           | VARCHAR2(44) |
| CONTINENT      | VARCHAR2(13) |
| REGION         | VARCHAR2(25) |
| SURFACEAREA    | NUMBER       |
| INDEPYEAR      | VARCHAR2(5)  |
| POPULATION     | NUMBER       |
| LIFEEXPECTANCY | VARCHAR2(4)  |
| GNP            | NUMBER       |
| GNPOLD         | VARCHAR2(9)  |
| LOCALNAME      | VARCHAR2(44) |
| GOVERNMENTFORM | VARCHAR2(44) |
| HEADOFSTATE    | VARCHAR2(32) |
| CAPITAL        | VARCHAR2(4)  |
| CODE2          | VARCHAR2(2)  |

***Solution***

```
SELECT country.continent, FLOOR(AVG(city.population)) FROM country, city WHERE city.countrycode = country.code GROUP BY country.continent;
```




