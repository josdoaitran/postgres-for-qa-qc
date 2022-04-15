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

- `BikeStores-create objects.sql`: this file is for creating database objects including schemas and tables.

- `BikeStores-load data.sql`: this file is for inserting data into the tables
- `BikeStores-drop all objects.sql`: this file is for removing the tables and their schemas from the sample database. It is useful when you want to refresh the sample database.

## References:
- https://www.sqlservertutorial.net/sql-server-sample-database/