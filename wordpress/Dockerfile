FROM wordpress:php7.4-apache

RUN set -ex; \
    apt update; \
    apt install -qqy --no-install-recommends \
        jq \
    ; \
    rm -rf /var/lib/apt/lists/*

RUN set -ex; \
    curl -sS -o /tmp/rds-combined-ca-bundle.pem "https://s3.amazonaws.com/rds-downloads/rds-combined-ca-bundle.pem"; \
    mkdir -p /usr/local/share/ca-certificates; \
    cd /usr/local/share/ca-certificates; \
    csplit -b %02d.crt -z -f rds-ca- /tmp/rds-combined-ca-bundle.pem '/-----BEGIN CERTIFICATE-----/' '{*}'; \
    update-ca-certificates; \
    rm -f /tmp/rds-combined-ca-bundle.pem

COPY docker-entrypoint.sh /usr/local/bin