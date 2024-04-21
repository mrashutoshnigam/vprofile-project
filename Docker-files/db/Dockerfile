# Use the official MySQL image as base
FROM mysql:8.0.33

LABEL "Project"="VProfile"
LABEL "Author"="Imran"

ENV MYSQL_ROOT_PASSWORD='vprodbpass'
ENV MYSQL_DATABASE="accounts"


# Set the working directory
WORKDIR /docker-entrypoint-initdb.d

# Copy the database initialize script: 
COPY db_backup.sql /docker-entrypoint-initdb.d/
