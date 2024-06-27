# SQL
Occupations - Hackerrank
WITH order_occupation
     AS (SELECT NAME,
                occupation,
                Row_number ()
                  OVER (
                    partition BY occupation
                    ORDER BY NAME) AS row_num
         FROM   occupations)
SELECT Max(CASE
             WHEN occupation = 'Doctor' THEN NAME
           END) AS Doctor,
       Max(CASE
             WHEN occupation = 'Professor' THEN NAME
           END) AS Professor,
       Max(CASE
             WHEN occupation = 'Singer' THEN NAME
           END) AS Singer,
       Max(CASE
             WHEN occupation = 'Actor' THEN NAME
           END) AS Actor
FROM   order_occupation
GROUP  BY row_num
ORDER  BY row_num;
