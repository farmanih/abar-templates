FROM nginx:alpine

EXPOSE 8080

RUN apk add --update --no-cache \
        bash \
        ca-certificates \
        wget \
        certbot \
    && \
    sed -i 's/listen\s*80/listen 8080/g' /etc/nginx/conf.d/default.conf && \
    chmod -R 777 /var/cache /var/run /usr/share/nginx/html && \
    mkdir -p /etc/letsencrypt /var/log/letsencrypt /var/lib/letsencrypt && \
    chmod -R g+w /etc/letsencrypt /var/log/letsencrypt /var/lib/letsencrypt

COPY run.sh run.sh

RUN chmod +x run.sh

USER 1001

CMD nginx && ./run.sh
