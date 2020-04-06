FROM nginx:alpine

# Replacing the default NginX configuration with the proxy configuration
RUN /bin/rm /etc/nginx/conf.d/default.conf
COPY proxy.conf /etc/nginx/conf.d/

# Security related resources
ADD certs /etc/nginx/certs
COPY htpasswd /etc/nginx/htpasswd

