
```bash
$ docker pull ubuntu:18.04
$ docker run --name pg-master -it -d IMAGE_ID
$ docker exec -it CONTAINER_ID bash
```

```bash
# service postgresql start 
```

```bash
# su - postgres -c "psql"  
psql (10.0)
Type "help" for help.

postgres=# 
```

```bash
postgres=# \password postgres
```
