# Type of Triangle

Source: https://www.hackerrank.com/challenges/what-type-of-triangle/problem?isFullScreen=true

Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

Equilateral: It's a triangle with 3 sides of equal length.
Isosceles: It's a triangle with 2 sides of equal length.
Scalene: It's a triangle with 3 sides of differing lengths.
Not A Triangle: The given values of A, B, and C don't form a triangle.

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

# Population Census

Source: https://www.hackerrank.com/challenges/asian-population/problem?isFullScreen=true

Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.

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
SELECT DISTINCT SUM(city.population) FROM country INNER JOIN city ON country.code = city.countrycode WHERE Country.Continent='Asia';
```

# Top Earners

Source: https://www.hackerrank.com/challenges/earnings-of-employees/problem?isFullScreen=true

We define an employee's total earnings to be their monthly salary * monthes worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as 2 space-separated integers.

***Input Format***

The Employee table containing employee data for a company is described as follows:

| Column      | Type    |
| ------------| --------|
| employee_id | Itneger |
| name        | String  |
| months      | Integer |
| salary      | Integer |

where employee_id is an employee's ID number, name is their name, months is the total number of months they've been working for the company, and salary is the their monthly salary.

***Solution**

```
SELECT MAX(months * salary), COUNT(months * salary) FROM Employee WHERE (months * salary) = (SELECT MAX(months * salary) FROM Employee);
```

# Higher Than 75 Marks

Source: https://www.hackerrank.com/challenges/more-than-75-marks/problem?isFullScreen=true

Query the Name of any student in STUDENTS who scored higher than 75 Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.

***Input Format***

The STUDENTS table is described as follows:

| Column | Type    |
| -------| --------|
| ID     | Itneger |
| Name   | String  |
| Marks  | Integer |

The Name column only contains uppercase (A-Z) and lowercase (a-z) letters.

***Solution***

```
SELECT name FROM students WHERE marks > 75 ORDER BY RIGHT(name, 3) ASC, id ASC;
```

# The PADS

Source: https://www.hackerrank.com/challenges/the-pads/problem?isFullScreen=true

Generate the following two result sets:

1. Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).
2. Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:
```
There are a total of [occupation_count] [occupation]s.
```
where `[occupation_count]` is the number of occurrences of an occupation in OCCUPATIONS and `[occupation]` is the lowercase occupation name. If more than one Occupation has the same `[occupation_count]`, they should be ordered alphabetically.

Note: There will be at least two entries in the table for each type of occupation.

***Input Format***

The OCCUPATIONS table is described as follows:

| Column     | Type   |
| -----------| -------|
| Name       | String |
| Occupation | String |

***Solution**

```
SELECT CONCAT(name, '(', SUBSTRING(occupation, 1, 1), ')') FROM occupations ORDER BY name;
SELECT CONCAT('There are a total of ', COUNT(occupation), ' ', LOWER(occupation), 's.') FROM occupations GROUP BY occupation ORDER BY COUNT(occupation), occupation;
```
