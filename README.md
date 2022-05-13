# Postgres For Qa/Qc

SQL database ussing Posgres - Simple Postgres  SQL for QA/QC for testing purpose

## Setup Local Database:

- Install Docker: https://docs.docker.com/desktop/
- Run pull Postgres SQL: `docker pull postgres`
- Start docker container: `docker run --name test-postgres -p 5432:5432 -e POSTGRES_PASSWORD=Password@12345 -d postgres`
- Db admin tool / Client DB tools by this comman:  `docker run --name pgadmin -p 5555:80 -e PGADMIN_DEFAULT_EMAIL="testingforevrything@gmail.com" -e PGADMIN_DEFAULT_PASSWORD="P@SS" dpage/pgadmin4`
- Db client tool `dbeaver`: https://dbeaver.io/download/

- Create database, table and import data
Open `setups` folder, we have 3 sql files:
    +  `create_db.sql`: this file is for creating database objects including schemas and tables.

    + `create_tables.sql`: this file is for creating the tables.
    + `import_data.sql`: this file is for importing data for all tables.
    + `relationship.sql`: this file is for removing the tables and their schemas from the sample database. It is useful when you want to refresh the sample database.

## Simple SQL command for QA:

### Select command

**Syntax**

- Select every thing:

```SELECT * FROM schema_name.table_name WHERE <condition>;```

- Select some fields :

```SELECT field1, field2 FROM schema_name.table_name WHERE <condition>;```

**Example:** 
```
select * from public.film;
select * from public.film limit 20;
select * from public.film where film_id = 45;
select * from public.film where title like 'Am%'
```

- SQL SELECT statement with expressions example
```
select first_name || ' ' || last_name from public.actor
```

## Order By

**Syntax**
```
SELECT
	select_list
FROM
	table_name
ORDER BY
	sort_expression1 [ASC | DESC],
        ...
	sort_expressionN [ASC | DESC];
```

Example: 
+ Order by 1 field and ASC is default option, when we don't mention type of odering.
```
SELECT * FROM public.customer ORDER BY last_name
```
+ Order by 1 field and DESC
```
SELECT * FROM public.actor ORDER BY first_name DECS, last_name ASC
```
## INNER JOIN:

Example for 2 tables: payment and staff to query data of payment for a staff_id.

```
SELECT
	staff.staff_id,
	first_name,
	last_name,
	amount,
	payment_date
FROM
	staff
INNER JOIN payment 
    ON payment.staff_id = staff.staff_id
ORDER BY payment_date;
``` 

## Group By:

We're going to group value from Select statement. We can use Group By. In the simple database, We can group data of payment table by customer_id, staff_id.

Example:
```
SELECT staff_id FROM payment Group By staff_id;
SELECT staff_id, sum(amount) FROM payment Group By staff_id;
```

## Insert:

Example:
```
INSERT INTO public.staff (staff_id, first_name, last_name, address_id, email, store_id, active, username, password, last_update, picture) VALUES ('3','Jack','Son','5','Jack.Son@sakilastaff.com','2','t','Jack','8cb2237d0679ca88db6464eac60da96345513964','2021-05-16 16:13:11.79328','');
```

## Delete:
```
Delete public.staff where staff_id = 3;
```

## Clear Table:
- Using Docker command to access to Postgres container: `docker exec -it test-postgres bash`
- Using this command to login Postgress database: `psql -d postgres -U  postgres -W` and input the password `Password@12345`
- Run this command to clear table: `DROP TABLE IF EXISTS **table_name** CASCADE;`
Example: `DROP TABLE IF EXISTS actor CASCADE;`
- Run this command multiple table: `DROP TABLE IF EXISTS inventory,rental,store CASCADE;`

## Clear Database:

`DROP DATABASE dvdrental;`

## References:
- https://drive.google.com/drive/folders/19MKLuRXCVp_1tCSkdktUy2choGV0SYcj
- https://www.sqlservertutorial.net/sql-server-sample-database/
- https://sqlserverguides.com/create-database-in-postgresql/