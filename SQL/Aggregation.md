# Aggregation

### 1. The Count Function
Query a count of the number of cities in CITY having a Population larger than .
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