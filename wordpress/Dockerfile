FROM wordpress:php7.4-apache

RUN set -ex; \
    apt update; \
    apt install -qqy --no-install-recommends \
        jq \
    ; \
    rm -rf /var/lib/apt/lists/*

COPY docker-entrypoint.sh /usr/local/bin