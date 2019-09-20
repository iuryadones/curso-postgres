
```bash
$ docker pull ubuntu:18.04
$ docker run --name pg-master -it -d IMAGE_ID
$ docker exec -it CONTAINER_ID bash
```

```bash
# apt update
# apt install postgresql-10
```

```bash
# service postgresql start 
```

```bash
# export PGDATA=/pgdata/10/data 
# mkdir -p $PGDATA
# chown -R postgres:postgres /pgdata
```

```bash
# service postgresql stop
```

```bash
# su - postgres
$ export PGDATA=/pgdata/10/data 
$ /usr/lib/postgresql/10/bin/initdb -D $PGDATA
```

```bash
# service postgresql start 
```

```bash
$ psql  
psql (10.0)
Type "help" for help.

postgres=# 
```

```bash
postgres=# \password postgres
```
