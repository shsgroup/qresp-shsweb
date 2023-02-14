FROM nginx:alpine

# Remove any existing config files
RUN rm /etc/nginx/conf.d/*

# Copy config files
# *.conf files in conf.d/ dir get included in main config
COPY ./default.conf /etc/nginx/conf.d/
COPY ./shsweb-servers.conf /etc/nginx/conf.d/
COPY ./archive-server.conf /etc/nginx/conf.d/

# mount shsweb, webpcet root directories
#RUN --mount=type=bind,source=/raid-disk/shs-archive,target=/usr/share/nginx/shs-archive,readonly
#RUN --mount=type=bind,source=/var/www/html,target=/usr/share/nginx/shsweb,readonly
#RUN --mount=type=bind,source=/var/www/webpcet/htdocs,target=/usr/share/nginx/webpcet,readonly
#COPY /raid-disk/shs-archive /usr/share/nginx/
#COPY /var/www/html /usr/share/nginx/
#COPY /var/www/webpcet/htdocs /usr/share/nginx/

# Add certificates and keys
RUN mkdir -p /etc/certs

COPY   ./shsweb_GlobalSign_Bundle.crt    /etc/certs/nginx.crt
COPY   ./shsweb_GlobalSign_private.key   /etc/certs/nginx.key
COPY   ./ssl_passwords.txt               /etc/certs/ssl_passwords.txt

# Expose the listening port
EXPOSE 443

# Launch NGINX
CMD [ "nginx", "-g", "daemon off;" ]
