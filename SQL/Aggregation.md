# Aggregation

### 1. The Count Function
Query a count of the number of cities in CITY having a Population larger than 100,000.
The CITY table is described as follows:

STATION: 
+------------+--------------+
|FIELD       | TYPE         |
+------------+--------------+
|ID          | NUMBER       |
-------------+--------------+
|NAME        | VARCHAR2(17) |
+------------+--------------+
|COUNTRYCODE | VARCHAR2(3)  |
-------------+--------------+
|DISTRICT    | VARCHAR2(20) |
+------------+--------------+
|POPULATION  | NUMBER       |
-------------+--------------+

#### Solution
SELECT COUNT(NAME)
FROM CITY
WHERE POPULATION > 100000
---------------------------------------------------------------------------
### 2. The Sum Function
Query the total population of all cities in CITY where District is California.

#### Solution
SELECT SUM(POPULATION)
FROM CITY
WHERE DISTRICT = "California"
---------------------------------------------------------------------------
### 3. Averages
Query the average population of all cities in CITY where District is California.

#### Solution
SELECT AVG(POPULATION)
FROM CITY
WHERE DISTRICT = "California"
---------------------------------------------------------------------------
### 4. Average Population
Query the average population for all cities in CITY, rounded down to the nearest integer.

#### Solution
SELECT FLOOR(AVG(POPULATION)) AS avg_population
FROM CITY;
--------------------------------------------------------------------------
### 5. Japan Population
Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

#### Solution
SELECT SUM(POPULATION)
FROM CITY
WHERE COUNTRYCODE = "JPN";
---------------------------------------------------------------------------
### 6. Population Density Difference
Query the difference between the maximum and minimum populations in CITY.

#### Solution
SELECT MAX(POPULATION) - MIN(POPULATION)
FROM CITY;
--------------------------------------------------------------------------