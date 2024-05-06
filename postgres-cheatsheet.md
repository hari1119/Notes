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
