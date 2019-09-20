# INSTALL IMAGE LINUX AND POSTGRES

Kernel linux - OS:

```bash
$ docker pull fedora:30
```

list images:

```bash
$ docker images
```

Run image fedora:

```bash
$ docker run -it IMAGE_ID
```

Execute em outro shell `docker ps`, depois volte ao shell do fedora e execute
`exit`, quando executamos `docker ps` a imagem linux não estará mais em
execução. Para continuar a execução mesmo saindo do shell da imagem linux do
docker, utilize `-d` no comando `docker run`.

Run image detach:

```bash
$ docker run -it -d IMAGE_ID
```

Execute bash:

```bash
$ docker exec -it CONTAINER_ID bash
```

obs:
você pode adicionar nome ao container, basta executar `docker run` com argumento
`--name`.

```bash
$ docker run --name pg-master -it -d IMAGE_ID
```

## POSTGRES

O `CONTAINER_ID` será a imagem do linux para instalação do postgres

```bash
$ docker exec -it CONTAINER_ID bash
```

install postgresql10-server

```bash
# dnf update
# rpm -Uvh https://yum.postgresql.org/10/fedora/fedora-30-x86_64/pgdg-fedora-repo-latest.noarch.rpm 
# dnf install postgresql10-server
```

init PGDATA

```bash
# mkdir -p /pgdata/10/data
# chown -R postgres:postgres /pgdata
```

```bash
# systemctl edit postgresql-10.service
```

editar o environment 

```
[Service]
Environment=PGDATA=/pgdata/10/data
```

init PGDATA

```bash
# /usr/pgsql-10/bin/postgresql-10-setup initdb
# ls /var/lib/pgsql/10/data/
# ls /pgdata/
```

```bash
# systemctl enable postgresql-10.service 
# systemctl start postgresql-10.service 
```

Testing:

```bash
# su - postgres -c "psql"  
psql (10.0)
Type "help" for help.

postgres=# 
```

```bash
postgres=# \password postgres
```

Se tiver algum problema instale outra imagem do fedora

```bash
$ docker pull fedora/systemd-systemd
$ docker run --name pgmaster -it -d IMAGE_ID
$ docker run --rm --privileged -ti -e 'container=docker' -v /sys/fs/cgroup:/sys/fs/cgroup:ro rawhide_systemd /bin/bash
```

obs: version fedora 24
```bash
# rpm -Uvh https://yum.postgresql.org/10/fedora/fedora-24-x86_64/pgdg-fedora-repo-latest.noarch.rpm 
```

References:

 - [install-postgres-fedora](https://tecadmin.net/install-postgresql-11-on-fedora/)
 - [most-useful-commands-postgres](https://www.technobytz.com/most-useful-postgresql-commands.html)
 - [config-master-slave-centos](https://www.howtoforge.com/tutorial/how-to-install-and-configure-master-slave-replication-with-postgresql-96-on-centos-7/)
 - [install-postgres-ubuntu](https://www.digitalocean.com/community/tutorials/como-instalar-e-utilizar-o-postgresql-no-ubuntu-16-04-pt)
 - [hub.docker/fedora](https://hub.docker.com/_/fedora)
