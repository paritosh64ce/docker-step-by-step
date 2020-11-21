
# docker build -t my-postgres .
# docker network create --driver bridge my-postgres-network
# docker run --name my-postgres-ctnr --network my-postgres-network -d my-postgres
# docker run -it --rm --network my-postgres-network my-postgres psql -h my-postgres -U postgresondocker --password postgresondocker



# =========================================================
# docker pull postgres
# docker run --name my-postgres -e POSTGRES_PASSWORD=password -d postgres
# docker ps
# docker exec -it my-postgres psql -U postgres
# #\l - list of databases
# #CREATE DATABASE myDb;
# #CREATE USER admin WITH ENCRYPTED PASSWORD 'my-password';
# #GRANT ALL PRIVILEGES ON DATABASE mydb TO admin;
# #CREATE TABLE my_table(id INT PRIMARY KEY, date DATE, tempC REAL, summary CHAR(20));
# #\d my_table
# #INSERT INTO my_table values (1, '2020-10-20', 38, 'Balmy');
# #INSERT INTO my_table values (2, '2020-10-21', 34, 'Mild');
# #INSERT INTO my_table values (3, '2020-10-22', -13, 'Scorching');
# #SELECT  * FROM my_table;

#FROM postgres:latest
# docker postgres:latest
# docker run -d --name pNode1 postgres:latest -e POSTGRES_PASSWORD=mysecretpassword -e POSTGRES_USER=postgress -e POSTGRES_DB=postgress -p 9432:5432


# =========================================================

# example Dockerfile for https://docs.docker.com/engine/examples/postgresql_service/
 
 
##FROM ubuntu:14.04
 
# Add the PostgreSQL PGP key to verify their Debian packages.
# It should be the same key as https://www.postgresql.org/media/keys/ACCC4CF8.asc
##RUN apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys B97B0AFCAA1A47F044F244A07FCC7D46ACCC4CF8
 
# Add PostgreSQL's repository. It contains the most recent stable release
#     of PostgreSQL, ``9.3``.
##RUN echo "deb http://apt.postgresql.org/pub/repos/apt/ precise-pgdg main" > /etc/apt/sources.list.d/pgdg.list
 
# Install ``python-software-properties``, ``software-properties-common`` and PostgreSQL 9.3
#  There are some warnings (in red) that show up during the build. You can hide
#  them by prefixing each apt-get statement with DEBIAN_FRONTEND=noninteractive
##RUN apt-get update && apt-get install -y python-software-properties software-properties-common postgresql-9.3 postgresql-client-9.3 postgresql-contrib-9.3
 
# Note: The official Debian and Ubuntu images automatically ``apt-get clean``
# after each ``apt-get``
 
# Run the rest of the commands as the ``postgres`` user created by the ``postgres-9.3`` package when it was ``apt-get installed``
##USER postgres
 
# Create a PostgreSQL role named ``postgresondocker`` with ``postgresondocker`` as the password and
# then create a database `postgresondocker` owned by the ``postgresondocker`` role.
# Note: here we use ``&&\`` to run commands one after the other - the ``\``
#       allows the RUN command to span multiple lines.
##RUN    /etc/init.d/postgresql start &&\
##    psql --command "CREATE USER postgresondocker WITH SUPERUSER PASSWORD 'postgresondocker';" &&\
##    createdb -O postgresondocker postgresondocker
 
# Adjust PostgreSQL configuration so that remote connections to the
# database are possible.
##RUN echo "host all  all    0.0.0.0/0  md5" >> /etc/postgresql/9.3/main/pg_hba.conf
 
# And add ``listen_addresses`` to ``/etc/postgresql/9.3/main/postgresql.conf``
##RUN echo "listen_addresses='*'" >> /etc/postgresql/9.3/main/postgresql.conf
 
# Expose the PostgreSQL port
##EXPOSE 5432
 
# Add VOLUMEs to allow backup of config, logs and databases
##VOLUME  ["/etc/postgresql", "/var/log/postgresql", "/var/lib/postgresql"]
 
# Set the default command to run when starting the container
##CMD ["/usr/lib/postgresql/9.3/bin/postgres", "-D", "/var/lib/postgresql/9.3/main", "-c", "config_file=/etc/postgresql/9.3/main/postgresql.conf"]

