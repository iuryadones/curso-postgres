# Postgres

Downloads:

 - [postgres](https://www.postgresql.org)

Reference:

 - [postgres/docs](https://www.postgresql.org/docs) 
 - [postgres/wiki](https://wiki.postgresql.org/wiki/)
 - [postgres/slides](https://wiki.postgresql.org/wiki/PostgreSQL_Related_Slides_and_Presentations)

## Run

Docker:

```bash
$ docker run --name curso-postgres -e POSTGRES_PASSWORD=asenha123 -d postgres
$ docker ps
$ docker exec -it curso-postgres bash
```

Acess postgres:

```bash
$ psql --username "postgres" 
```

or

```bash
$ su - postgres
$ psql
```

VarIn docker postgres:

 - `POSTGRES_DB`
 - `POSTGRES_INITDB_ARGS`
 - `POSTGRES_PASSWORD`
 - `POSTGRES_PASSWORD_FILE`
 - `POSTGRES_USER`

## psql

comando de help

```bash
postgres# \?
```

