ARG ADDON_VERSION=1.86.1
FROM docker.n8n.io/n8nio/n8n:${ADDON_VERSION}
USER root
RUN apk add --no-cache --update jq bash npm
WORKDIR /data
COPY docker-entrypoint.sh /tmp/docker-entrypoint.sh
ENTRYPOINT ["bash", "/tmp/docker-entrypoint.sh"]
EXPOSE 5678/tcp
