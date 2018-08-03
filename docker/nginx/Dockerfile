# Base image
FROM nginx
# Install dependencies
RUN apt-get update -qq && apt-get -y install apache2-utils
# establish where should look for files
ENV RAILS_ROOT=/app
# set our working directory inside the image
WORKDIR $RAILS_ROOT
# create log directory
# RUN mkdir publicdocke
# copy over static assets
# COPY public /public/
# copy nginx config template
COPY docker/nginx/nginx.conf /tmp/docker.nginx
# substitute variable references in the Nginx config template for real value from the environment
# put the final config in its places
RUN envsubst '$RAILS_ROOT' < /tmp/docker.nginx > /etc/nginx/conf.d/default.conf
EXPOSE 80
# use the "exec" from of CMD so nginx shuts down gracefully on SIGTERM(i.e. 'docker stop')
CMD [ "nginx", "-g", "daemon off;" ]