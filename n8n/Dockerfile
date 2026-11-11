ARG BUILD_VERSION
FROM alpine:3.24 AS apk-tools
RUN apk add --no-cache apk-tools-static

FROM docker.io/n8nio/n8n:${BUILD_VERSION}
USER root
COPY --from=apk-tools /sbin/apk.static /tmp/apk
COPY --from=apk-tools /etc/apk/keys/ /tmp/apk-keys/
RUN /tmp/apk --keys-dir /tmp/apk-keys --repositories-file /dev/null \
    --repository https://dl-cdn.alpinelinux.org/alpine/v3.24/main \
    --no-cache add jq bash \
    && rm -rf /tmp/apk /tmp/apk-keys
WORKDIR /data
COPY docker-entrypoint.sh /tmp/docker-entrypoint.sh
ENTRYPOINT ["bash", "/tmp/docker-entrypoint.sh"]
EXPOSE 5678/tcp
