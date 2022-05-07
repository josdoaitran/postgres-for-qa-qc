# Postgres For Qa/Qc

SQL database ussing Posgres - Simple Postgres  SQL for QA/QC for testing purpose

## Esentials:

- Install Docker: https://docs.docker.com/desktop/
- Run pull Postgres SQL: `docker pull postgres`
- Start docker container: `docker run --name test-postgres -p 5432:5432 -e POSTGRES_PASSWORD=Password@12345 -d postgres`
- Db admin tool / Client tools by this comman:  `docker run --name pgadmin -p 5555:80 -e PGADMIN_DEFAULT_EMAIL="testingforevrything@gmail.com" -e PGADMIN_DEFAULT_PASSWORD="P@SS" dpage/pgadmin4`
- Db client tool `dbeaver`: https://dbeaver.io/download/

- ERD Extension of VS Code: https://marketplace.visualstudio.com/items?itemName=dineug.vuerd-vscode

## Setup Local Database:
Open `setups` folder, we have 3 sql files:

- `create_db.sql`: this file is for creating database objects including schemas and tables.
- `create_tables.sql`: this file is for creating the tables.
- `import_data.sql`: this file is for importing data for all tables.
- `relationship.sql`: this file is for removing the tables and their schemas from the sample database. It is useful when you want to refresh the sample database.



## Clear Table:
- Using Docker command to access to Postgres container: `docker exec -it test-postgres bash`
- Using this command to login Postgress database: `psql -d postgres -U  postgres -W` and input the password `Password@12345`
- Run this command to clear table: `DROP TABLE IF EXISTS **table_name** CASCADE;`
Example: `DROP TABLE IF EXISTS actor CASCADE;`
- Run this command multiple table: `DROP TABLE IF EXISTS inventory,rental,store CASCADE;`

## Clear Database:

`DROP DATABASE dvdrental;`

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
select * from public.film where film_id = 45;
select * from public.film where title like 'Am%'
```


## References:
- https://drive.google.com/drive/folders/19MKLuRXCVp_1tCSkdktUy2choGV0SYcj
- https://www.sqlservertutorial.net/sql-server-sample-database/
- https://sqlserverguides.com/create-database-in-postgresql/