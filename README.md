# Postgres For Qa/Qc

SQL database ussing Posgres - Simple Postgres  SQL for QA/QC for testing purpose

## Esentials:

- Install Docker: https://docs.docker.com/desktop/
- Run pull Postgres SQL: `docker pull postgres`
- Start docker container: `docker run --name test-postgres -p 5432:5432 -e POSTGRES_PASSWORD=Password@12345 -d postgres`
- Db admin tool / Client tools by this comman:  `docker run --name pgadmin -p 5555:80 -e PGADMIN_DEFAULT_EMAIL="josdoaitran@gmail.com" -e PGADMIN_DEFAULT_PASSWORD="P@SS" dpage/pgadmin4`
- Db client tool `dbeaver`: https://dbeaver.io/download/
