FROM debian:jessie
MAINTAINER Sven Dowideit <SvenDowideit@home.org.au>

# from https://github.com/nginxinc/docker-nginx/blob/master/Dockerfile
# BUT installing nginx-full
RUN apt-key adv --keyserver hkp://pgp.mit.edu:80 --recv-keys 573BFD6B3D8FBC641079A6ABABF5BD827BD9BF62
RUN echo "deb http://nginx.org/packages/mainline/debian/ jessie nginx" >> /etc/apt/sources.list
RUN apt-get update \
	&& apt-get install -y nginx-full \
	&& apt-get clean \
	&& rm -rf /var/lib/apt/lists/*

# forward request and error logs to docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
	&& ln -sf /dev/stderr /var/log/nginx/error.log

# Improves performance by declaring an explicit volume that bypasses docker's copy-on-write backend (e.g. aufs)
# and bind-mounts the data directly from the host filesystem.
VOLUME ["/var/cache/nginx"]
EXPOSE 80 443

ENTRYPOINT ["nginx", "-g", "daemon off;"]
