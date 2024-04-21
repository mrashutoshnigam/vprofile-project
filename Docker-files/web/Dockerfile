# Use the official nginx image as a base
FROM nginx:latest

LABEL "Project"="VProfile"
LABEL "Author"="Imran"

RUN rm -rf /etc/nginx/conf.d/default.conf
COPY nginvproapp.conf /etc/nginx/conf.d/vproapp.conf
