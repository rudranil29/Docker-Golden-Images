ARG DEBIAN_IMAGE=debian:jessie-slim
FROM $DEBIAN_IMAGE

RUN apt-get update && apt-get install -y nginx \
    && rm -rf /var/lib/apt/lists/* \
    && rm /etc/nginx/sites-enabled/default
COPY docker-utils/conf/nginx.conf /etc/nginx/nginx.conf
EXPOSE 80 443
CMD ["nginx", "-g", "daemon off;"]
