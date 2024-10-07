![image](https://github.com/user-attachments/assets/393a117b-201a-4998-a8b2-3f1f2b672a68)


# Postgress

### To Install Postgres

``` sudo apt install postgresql postgresql-contrib ```

### Use the below commands to Create a user in for postgres.

- ``` sudo su postgres ``` 
- ``` createuser -s user_name ```
- ``` psql -l ```
- ``` psql template1 ```
- ``` alter role user_name with password 'p@s$w0rd';```

### Get into Postress user
- ``` sudo -i -u postgres ```
- ``` psql ```
- List Database ``` \l ```
- Connect to Database ``` \c db_name ```
- Quit from the Database ```\q ```
- Expend the display screen ``` \x ```

## Compare From date and To date

``` from >= "value" and to <= "value" ```

### REPLACE & ARRAY_REPLACE

- The REPLACE function is great for modifying parts of a string, such as correcting typos or standardizing values. ARRAY_REPLACE is a similar function used for replacing elements in an array. This is particularly useful when dealing with ARRAY type fields such as an array of strings or ints.
 
#### Syntax:
```
 REPLACE(input_string, string_to_replace, replacement_string)
 ARRAY_REPLACE(input_array, element_to_replace, replacement_element)
```

#### Example:
```postgresql
SELECT REPLACE('Bartolomeo Messi', 'Bartolomeo', 'Lionel') AS greeting;
-- OUTPUT
| greeting     |
| ------------ |
| Lionel Messi |

SELECT REPLACE(ARRAY[1,2,3,4,5], 3, 4) AS new_array;
-- OUTPUT
| new_array   |
|-------------|
| {1,2,4,4,5} |
```
### CTE
- Common Table Expression (CTE) is a temporary result set that can be referenced further down in the query. They allow you to temporarily store query results to be used & referenced in another part of the query. They are especially useful for making complex queries more readable.

#### Syntax:
```
WITH cte_name AS ( -- defining cte
    SELECT column1, column2, ...
    FROM table_name
    WHERE condition
)
SELECT column1, column2, ...
FROM cte_name; -- referencing cte here
```

#### Example
```
-- QUERY: top 10 defenders with CTEs
WITH barca_player_ids AS (
-- get the barca palyer ids first
  SELECT player_id FROM player_club_mapping
  WHERE club_name = 'FC_Barcelona'
), 
top_barca_defs AS (
-- getting top 10 barca defs using game stats table
  SELECT player_id, AVG(attribute_value) def_stats FROM game_stats
  WHERE
    player_id IN (SELECT player_id FROM barca_player_ids)
    AND attribute_name IN ('Defense', 'Pace', 'Tackle', 'Physicality')
  GROUP BY player_id
  ORDER BY AVG(attribute_value) DESC
  LIMIT 10
)
-- joining the top 5 defenders with their names to produce the final result
SELECT name, contract_duration FROM players p
INNER JOIN top_barca_defs tbd
  ON tbd.player_id = p.id
ORDER BY tbd.def_stats DESC;

-- OUTPUT:
| name                                 | contract duration |
|--------------------------------------|-------------------|
| Gerard Pique                         |  2008-now         |
| Dani Alves                           |  2008–now         |
| Rafa Marquez                         |  2003–2010        |
| Carles Puyol                         |  1999–now         |
| Michael Reiziger                     |  1997–2004        |
| Ronald "Tintin" Roeman               |  1989–1995        |
| Miguel "Migueli" Bernardo Bianquetti |  1973–1988        |
| Antoni Torres                        |  1965–1976        |
| Sigfrid Gracia                       |  1952–1966        |
| Joan Segarra                         |  1949–1964        |
```
- Example: First we get the player_ids of all barca players using ```barca_player_ids CTE```. Then, we get the top barca defenders using the average defence-related attributes of barca players using top_barca_defs CTE. Finally, we select the player name and contract duration using those ```top_barca_def``` IDs and the ```players``` table.

### VALUES JOIN
- The VALUES clause is commonly used to insert multiple rows into a table. However, its capabilities extend beyond insert statements. I recently discovered that they can be treated as static tables and joined with other tables. This blew my mind.
- The following example shows how to add external columns to your fetch query. Suppose you have a table ```players``` which holds ```player_id```, ```name```, and ```player position```. You have the date of birth (DOB) for these players in an external file and want to view it alongside the DB columns. Here’s how you can do it using VALUES clause.

#### Example: Showing DOBs of players alongside
```
-- QUERY
SELECT p.player_id, v.name, p.position, v.dob, v.gender FROM players p
INNER JOIN ( VALUES
  ('Ronaldo', '1985-02-05', 'M'),
  ('Messi', '1987-06-24', 'M')
) AS v(name, dob, gender)
ON p.name = v.name;
-- using it add columns that doesn't exists in the players table
-- in the select output

-- OUTPUT
| player_id | name    | position             | dob       | gender |
|-----------|---------|----------------------|-----------|--------|
| 1         | Messi   | Attacking Midfielder |1985-02-05 | M      |
| 2         | Ronaldo | Winger               |1987-06-24 | M      |
```

### BATCH UPDATE
- For some reason, batch updates with raw SQL are always something that I struggle with. Although I don’t use it all the time, it is a really useful query when needed.
  
#### Example: Update player salary in ```players``` table using another table ```salary_updates```
```
-- QUERY: batch update using another table
UPDATE players p
SET salary = su.new_salary
FROM salary_updates su
WHERE p.player_id = su.player_id;
-- where condition is used to join the two tables
```
- Explanation: The above query updates the ```salary``` column in the ```players``` table based on the data from the ```salary_updates``` table. It joins the two tables on ```player_id``` to apply the new salary values to the corresponding players.

#### Example: Updating player’s club in batch using VALUES clause
```
-- QUERY: batch update using the values clause
UPDATE players
SET club = new_values.club
( VALUES
  ('Lionel Messi', 'Inter Miami FC'),
  ('Cristiano Ronaldo', 'Al-Nassr FC')
) AS new_values(player_name, club)
WHERE players.name = new_values.player_name;
```
- Explanation: You can also use ```VALUES``` clause to do a similar thing. The query above updates the ```club``` column in the players table using static data provided in the ```VALUES``` clause. It joins the static values with the ```players``` table on ```name``` to apply the new club values to the corresponding players.
