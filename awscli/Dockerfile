FROM alpine:latest
# MAINTAINER Jessica Frazelle <jess@docker.com>
MAINTAINER Sven Dowideit <SvenDowideit@home.org.au>

RUN apk update && apk add \
	ca-certificates \
	groff \
	less \
	python \
	py-pip \
	&& rm -rf /var/cache/apk/* \
	&& pip install awscli

ENTRYPOINT [ "aws" ]
