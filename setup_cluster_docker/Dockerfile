FROM ubuntu:16.04

RUN  apt-get update \
     && apt-get install -y wget \
     && apt-get install -y software-properties-common
RUN sh -c "echo 'deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -c -s`-pgdg main' >> /etc/apt/sources.list.d/pgdg.list"
RUN wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
# RUN apt-get update

# Add our PPA
RUN add-apt-repository ppa:timescale/timescaledb-ppa
RUN apt-get update

# To install for PG 10.2+
RUN apt-get install -y timescaledb-postgresql-10

USER postgres

RUN echo "shared_preload_libraries = 'timescaledb'" >> /etc/postgresql/10/main/postgresql.conf

EXPOSE 5432

# CMD systemctl restart postgresql
CMD ["/usr/lib/postgresql/10/bin/postgres", "-D", "/var/lib/postgresql/10/main", "-c", "config_file=/etc/postgresql/10/main/postgresql.conf"]
