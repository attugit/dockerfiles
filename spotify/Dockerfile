FROM debian:testing

ADD https://github.com/Yelp/dumb-init/releases/download/v1.2.0/dumb-init_1.2.0_amd64.deb /tmp/dumb-init_1.2.0_amd64.deb

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      gnupg2 && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0DF731E45CE24F27EEEB1450EFDC8610341D9410 && \
    echo "deb http://repository.spotify.com stable non-free" >> /etc/apt/sources.list.d/spotify.list && \
    apt-get update && apt-get install -y --no-install-recommends \
        libx11-xcb1 \
	spotify-client && \
    dpkg -i /tmp/dumb-init_1.2.0_amd64.deb && \
    rm /tmp/dumb-init_1.2.0_amd64.deb && \
    groupadd -r spotify && \
    useradd -rmg spotify -G audio,video spotify && \
    rm -rf /var/lib/apt/lists/*

USER spotify
ENTRYPOINT ["dumb-init", "--"]
CMD [ "spotify" ]
