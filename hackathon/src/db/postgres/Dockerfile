# TODO

# We use Postgres for the database, version 11.6 - it can use a minimal OS.

FROM postgres:14-alpine

# There's an init script in this folder which populates the reference data:
#  init-products-db.sh
COPY ./init-products-db.sh /docker-entrypoint-initdb.d/

ENV POSTGRES_PASSWORD='widgetario'

# Your base image should make it easy to run that script as part of the container startup.