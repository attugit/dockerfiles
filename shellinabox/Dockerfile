FROM debian:testing

ADD https://github.com/Yelp/dumb-init/releases/download/v1.2.0/dumb-init_1.2.0_amd64.deb /tmp/dumb-init_1.2.0_amd64.deb

RUN \
    apt-get update \
    && apt-get install -y shellinabox \
    && rm -rf /var/lib/apt/lists/* \
    && dpkg -i /tmp/dumb-init_1.2.0_amd64.deb \
    && rm /tmp/dumb-init_1.2.0_amd64.deb

ENTRYPOINT ["dumb-init", "--"]

