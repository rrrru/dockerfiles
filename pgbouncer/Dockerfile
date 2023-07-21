FROM ubuntu:22.04

RUN apt update && apt install wget gnupg2 -y

RUN sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list' \
  &&  wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add - \
  &&  apt-get -qy dist-upgrade && apt install pgbouncer -yq --no-install-recommends && apt-get -qy clean \
  &&  rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN mkdir -p /var/log/postgresql
RUN chmod -R 755 /var/log/postgresql
RUN chown -R postgres:postgres /var/log/postgresql


ENV PG_CONFIG /etc/pgbouncer/pgbouncer.ini
ENV PG_USER postgres

USER postgres
ENTRYPOINT pgbouncer -u $PG_USER $PG_CONFIG
