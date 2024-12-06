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

### Window Functions
- Window functions are powerful tools that allow you to perform calculations across a set of table rows based on the value of a particular column. However, unlike group by, they do not collapse rows into a single result.

#### Example: Comparing the average salary of a club vs player's individual salary
```
-- QUERY: window function (partition by)
SELECT 
    id,
    name,
    salary,
    AVG(salary) OVER (PARTITION BY club) AS avg_salary_by_club,
    club
FROM players;
-- OUTPUT
| id | name     | salary   | av_salary_by_club | club    |
|----|----------|----------|-------------------|---------|
| 1  | Alvarez  | 20,000   | 100,000           | BFC     |     
| 2  | Swarez   | 180,000  | 100,000           | BFC     |
| 3  | Rodrique | 20,000   | 25,000            | RFC     |
| 4  | Modrique | 30,000   | 25,000            | RFC     |

-- as you can see, avg salary by
-- club (the partition by column) is calculated 
-- then it is added to all players that belong
-- to the club & not grouped by the club.

-- contrast with group by query
SELECT club, AVG(salary) FROM players GROUP BY club;
-- OUTPUT
| av_salary_by_club | club    |
|-------------------|---------|
| 100,000           | BFC     |   
| 25,000            | RFC     |
```
- **Explanation**: This query calculates the average salary for each club while still returning individual player records, allowing you to compare each employee’s salary to the club’s average.

### Delete Duplicates
- All developers come across a time when they need to clean up duplicates in a table. Here’s how you can clean up duplicate records. In the first scenario, we have multiple records in the ```players``` table with the same ```name```, ```jersey_number``` and ```club```. We want to resolve this by keeping the latest inserted data and removing the old ones.

#### Example:
```
-- QUERY: deleting duplicate players only keeping the latest records
WITH duplicates AS (
    SELECT
       id,
      ROW_NUMBER() OVER (
        PARTITION BY name, jersey_number, club
        ORDER BY insert_date DESC
      ) AS rn
    FROM active_players
)
DELETE FROM players
WHERE id IN (
    SELECT id FROM duplicates
    WHERE rn > 1
);
```
- What if even the ID column is duplicated? Well, there’s a system column that PostgreSQL uses to keep track of records called **ctid**. This column is always unique. We can use this to delete the duplicates as shown below.

```
-- QUERY: identifies duplicates and removes them while keeping the first occurrence.
WITH duplicates AS (
    SELECT
      ctid,
      ROW_NUMBER() OVER (
        PARTITION BY id, name, jersery_number, club
        ORDER BY ctid DESC
      ) AS rn
    FROM players
)
DELETE FROM players
WHERE ctid IN (
    SELECT ctid FROM duplicates
    WHERE rn > 1
);
```
### Using RETURNING in Update and Delete Queries
- The ```RETURNING``` clause allows you to immediately retrieve the affected rows after an ```UPDATE``` or ```DELETE``` operation. This is useful for logging or further processing the modified data. I use it to make sure I correctly changed the tables after running delete and update queries.

#### Example:
```
-- QUERY: returning the updated records
UPDATE players
SET age += 1
WHERE id = 1001
RETURNING id, name, age;
-- OUTPUT
| id | name    | age |
|----|---------|-----|
| 1  | Ronaldo | 50  |

-- QUERY: returning deleted records
DELETE FROM employees
WHERE id = 5
RETURNING id, name;
-- OUTPUT
| id | name    |
|----|---------|
| 5  | Diwash  |
```

### Adding a Serial Number Using ROW_NUMBER
- On my first ever job, I needed to add a serial number in a ```SELECT``` query. I was trying to do some calculations, though I can’t remember exactly what they were. I tried for like 30 minutes and couldn’t figure it out. A senior developer eventually helped me solve the issue without needing the serial number at all.

#### Example:
```
-- QUERY
SELECT *, ROW_NUMBER() OVER (PARTITION BY 1) AS rn
FROM diwash_test;
-- OR more simply
SELECT *, ROW_NUMBER() OVER () AS rn
FROM diwash_test;
-- OUTPUT
| id | name       | rn |
|----|------------|----|
| 1  | Messi      | 1  |
| 2  | Ronaldo    | 2  |
| 3  | Dembele    | 3  |
| 5  | Bellingham | 4  |
| 7  | Mbappe     | 5  |
```

### ARRAY_AGG & ARRAY CONTAINS(@>)
- The ```ARRAY_AGG``` function is useful for aggregating values into an array. This is definitely the one aggregation function that I use the most.

#### Example: Find the players who have played for both Real Madrid and Barcelona, along with a list of all the clubs they have played for.
```
-- QUERY
SELECT player_name, ARRAY_AGG(club) clubs FROM player_club_mappings
GROUP BY player_name
HAVING ARRAY_AGG(club) @> ARRAY['Barcelona', 'Real Madrid']
LIMIT 3

-- @> Operator: This is the "contains" operator for arrays
-- in PostgreSQL. It verifies if the aggregated array
-- includes all elements of the specified array
-- (ARRAY['Barcelona', 'Real Madrid']).

-- OUTPUT
| player_name     | clubs                                                                                                          |
|-----------------|----------------------------------------------------------------------------------------------------------------|
| Ronaldo Nazario | {Corinthians, Cruzeiro, Palmeiras, PSV Eindhoven, Barcelona, Inter Milan, Real Madrid, AC Milan}               |
| Samuel Eto''o   | {Kadji Sports, Union Douala, Canon Yaoundé, Real Madrid, Mallorca, Barcelona, Inter Milan,...}                 |
| Bernd Schuster  | {1. FC Köln, Hamburger SV, Real Madrid, Barcelona, Paris Saint-Germain, Austria Wien, FC Wil, Atlético Madrid} |
```

- Explanation: This query aggregates all the clubs that players have played in using ```ARRAY_AGG``` . Then, it filters out only the players that have played with both Barcelona and Real Madrid using```@>``` (array contains).

### SPLIT_PART
- The ```SPLIT_PART``` function allows you to split a string on a specified delimiter and return the nth substring. This is useful for extracting parts of a string, such as pulling out domain names from email addresses.

#### Example: Pulling out domain names from email addresses
```
-- QUERY
SELECT name, email, SPLIT_PART(email, '@', 2) email_domain AS domain
FROM players
LIMIT 3;
-- OUTPUT
| name    | email             | email_domain  |
|---------|-------------------|---------------|
| Diwash  | diwash@gmail.com  | gmail.com     |
| Hari    | hari@outlook.com  | outlook.com   |
| Rudra   | rudra@discord.com | discord.com   |
```

### Enabled audit log in the DB.
- Audit log used to tracking the Create, Delete,Update changes in the Data.
![image](https://github.com/user-attachments/assets/bfe5c0b4-9440-4ccd-ae78-a3a969dd59ba)

- **Step 1: Create an Audit Schema and Table**
    ```sql
    -- Create a schema named "audit"
    CREATE SCHEMA audit;
    REVOKE CREATE ON SCHEMA audit FROM public;

    CREATE TABLE audit.logged_actions (
        schema_name TEXT NOT NULL,
        table_name TEXT NOT NULL,
        record_id INTEGER NOT NULL,
        user_name TEXT,
        action_tstamp TIMESTAMP WITH TIME ZONE NOT NULL DEFAULT CURRENT_TIMESTAMP,
        action TEXT NOT NULL CHECK (action IN ('I', 'D', 'U')),
        original_data TEXT,
        new_data TEXT,
        query TEXT
    ) WITH (fillfactor=100);

    REVOKE ALL ON audit.logged_actions FROM public;
    GRANT SELECT ON audit.logged_actions TO public;
    ```
 - This logged_actions table will store the details of each change. The action column will record the type of action (I for insert, D for delete, U for update). You can add indexes on frequently queried columns for optimized performance.
   ```sql
   CREATE INDEX logged_actions_schema_table_idx
   ON audit.logged_actions(((schema_name || '.' || table_name)::TEXT));

   CREATE INDEX logged_actions_action_tstamp_idx 
   ON audit.logged_actions(action_tstamp);

   CREATE INDEX logged_actions_action_idx 
   ON audit.logged_actions(action);
   ```
- **Step 2: Define the Trigger Function**
  - The following trigger function will insert a record into audit.logged_actions every time a row in the target table is modified.
  ```sql
  CREATE OR REPLACE FUNCTION audit.log_current_action() RETURNS trigger AS $body$
  DECLARE
    v_old_data TEXT;
    v_new_data TEXT;
  BEGIN
    IF (TG_OP = 'UPDATE') THEN
        v_old_data := ROW(OLD.*);
        v_new_data := ROW(NEW.*);
        INSERT INTO audit.logged_actions 
        (schema_name, table_name, record_id, user_name, action, original_data, new_data, query)
        VALUES 
        (TG_TABLE_SCHEMA::TEXT, TG_TABLE_NAME::TEXT, NEW.id, session_user::TEXT, substring(TG_OP,1,1), v_old_data, v_new_data, current_query());
        RETURN NEW;
    ELSIF (TG_OP = 'DELETE') THEN
        v_old_data := ROW(OLD.*);
        INSERT INTO audit.logged_actions 
        (schema_name, table_name, record_id, user_name, action, original_data, query)
        VALUES 
        (TG_TABLE_SCHEMA::TEXT, TG_TABLE_NAME::TEXT, OLD.id, session_user::TEXT, substring(TG_OP,1,1), v_old_data, current_query());
        RETURN OLD;
    ELSIF (TG_OP = 'INSERT') THEN
        v_new_data := ROW(NEW.*);
        INSERT INTO audit.logged_actions 
        (schema_name, table_name, record_id, user_name, action, new_data, query)
        VALUES 
        (TG_TABLE_SCHEMA::TEXT, TG_TABLE_NAME::TEXT, NEW.id, session_user::TEXT, substring(TG_OP,1,1), v_new_data, current_query());
        RETURN NEW;
    ELSE
        RAISE WARNING '[AUDIT.LOG_CURRENT_ACTION] - Other action occurred: %, at %', TG_OP, now();
        RETURN NULL;
    END IF;
   EXCEPTION
    WHEN data_exception THEN
        RAISE WARNING '[AUDIT.LOG_CURRENT_ACTION] - Data Exception';
        RETURN NULL;
    WHEN unique_violation THEN
        RAISE WARNING '[AUDIT.LOG_CURRENT_ACTION] - Unique Violation';
        RETURN NULL;
    WHEN others THEN
        RAISE WARNING '[AUDIT.LOG_CURRENT_ACTION] - Other Exception';
        RETURN NULL;
   END;
   $body$
   LANGUAGE plpgsql
   SECURITY DEFINER
   SET search_path = pg_catalog, audit;
  ```
 - Step 3: Attach Triggers to Tables
   - Add this trigger function to each table you want to audit:
   ```sql
   CREATE TRIGGER tablename_audit
   AFTER INSERT OR UPDATE OR DELETE ON tablename
    FOR EACH ROW EXECUTE FUNCTION audit.log_current_action();
   ```
   [Link](https://medium.com/@ihcnemed/postgresql-record-every-change-in-your-database-a98a6586527c)


