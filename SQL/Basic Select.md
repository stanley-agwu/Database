# Basic Select

### 1. Weather Observation Station 3
Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.
The STATION table is described as follows:

STATION: 
+------------+--------------+
|FIELD       | TYPE         |
+------------+--------------+
|CITY        | VARCHAR2(21) |
-------------+--------------+
|STATE       | VARCHAR2(21) |
+------------+--------------+
|LAT_N       | NUMBER       |
-------------+--------------+
|LONG_W      | NUMBER       |
+------------+--------------+

->
SELECT DISTINCT CITY
FROM STATION
WHERE ID % 2 = 0;
---------------------------------------------------------------------
### 2. Weather Observation Station 4
Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table.
The STATION table is described as follows:

Station.jpg

where LAT_N is the northern latitude and LONG_W is the western longitude.

For example, if there are three records in the table with CITY values 'New York', 'New York', 'Bengalaru', there are 2 different city names: 'New York' and 'Bengalaru'. The query returns , because total number of records - number of unique city names = 3 - 2 = 1

->
SELECT COUNT(CITY) - COUNT(DISTINCT CITY)
FROM STATION
------------------------------------------------------------------------
### 3. Weather Observation Station 5
Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.

Sample Input
For example, CITY has four entries: DEF, ABC, PQRS and WXY.

Sample Output
ABC 3
PQRS 4
Explanation

When ordered alphabetically, the CITY names are listed as ABC, DEF, PQRS, and WXY, with lengths  and . The longest name is PQRS, but there are  options for shortest named city. Choose ABC, because it comes first alphabetically.

Note
You can write two separate queries to get the desired output. It need not be a single query.

->
##### Goal
Return:
1. City with the shortest name and its length
2. City with the longest name and its length
3. If there are ties, choose the city that comes first alphabetically.

##### Solution (Two Queries — Recommended)
1. City with the shortest name

SELECT CITY, LENGTH(CITY)
FROM STATION
ORDER BY LENGTH(CITY) ASC, CITY ASC
LIMIT 1;

2. City with the longest name

SELECT CITY, LENGTH(CITY)
FROM STATION
ORDER BY LENGTH(CITY) DESC, CITY ASC
LIMIT 1;

3. Combined Output (Single Result Set)

If platform allows UNION ALL, you can combine them:

(
    SELECT CITY, LENGTH(CITY)
    FROM STATION
    ORDER BY LENGTH(CITY) ASC, CITY ASC
    LIMIT 1
)
UNION ALL
(
    SELECT CITY, LENGTH(CITY)
    FROM STATION
    ORDER BY LENGTH(CITY) DESC, CITY ASC
    LIMIT 1
);
----------------------------------------------------------------------
### 4. Weather Observation Station 6
Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION table. Your result cannot contain duplicates.

->
SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '^[AEIOUaeiou]';
-------------------------------------------------------------------------
### 5. Weather Observation Station 7
Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

->
SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '[AEIOUaeiou]$';
----------------------------------------------------------------------------
### 6. Weather Observation Station 8
Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.

->
SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '^[AEIOUaeiou]' AND CITY REGEXP '[AEIOUaeiou]$';
----------------------------------------------------------------------------
### 7. Weather Observation Station 9
Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.

->
SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '^[^AEIOUaeiou]';

Alternatively use ->

SELECT DISTINCT CITY
FROM STATION
WHERE CITY NOT REGEXP '^[AEIOUaeiou]';
------------------------------------------------------------------------------
### 8. Weather Observation Station 10

Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.

->
SELECT DISTINCT CITY
FROM STATION
WHERE CITY NOT REGEXP '[AEIOUaeiou]$';

Alternatively use ->

SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '[^AEIOUaeiou]$';
-----------------------------------------------------------------------------
### 9. Weather Observation Station 11

Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

->
SELECT DISTINCT CITY
FROM STATION
WHERE CITY NOT REGEXP '^[AEIOUaeiou]' OR CITY NOT REGEXP '[AEIOUaeiou]$';

Alternatively use ->

SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '^[^AEIOUaeiou]' OR CITY REGEXP '[^AEIOUaeiou]$';
-----------------------------------------------------------------------------
### 10. Weather Observation Station 12

Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

->
SELECT DISTINCT CITY
FROM STATION
WHERE NOT CITY REGEXP '^[AEIOUaeiou]' AND NOT CITY REGEXP '[AEIOUaeiou]$';
-----------------------------------------------------------------------------
