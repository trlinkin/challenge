FROM nginx:alpine

# Remove the original NginX Configuration
RUN /bin/rm /etc/nginx/conf.d/default.conf

# Add custom configuration for secure application, restrict the sources from which the content can be accessed to the Docker bridge addresses.
COPY secure.conf /etc/nginx/conf.d/
COPY access.conf /etc/nginx/conf.d/

# Adding the Application context
ADD app /usr/share/nginx/secure/app
