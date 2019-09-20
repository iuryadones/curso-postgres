FROM ubuntu:latest

# EXPOSE

RUN apt update
RUN apt install postgresql-10 postgresql-contrib -y

ENV PGDATA=/pgdata/10/data

RUN mkdir -p $PGDATA
RUN chown -R postgres:postgres /pgdata

USER postgres

ENV PGDATA=/pgdata/10/data
RUN /usr/lib/postgresql/10/bin/initdb -D $PGDATA

USER root

RUN service postgresql start

USER postgres
CMD ["psql"]

