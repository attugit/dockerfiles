FROM debian:testing

ADD https://github.com/Yelp/dumb-init/releases/download/v1.2.0/dumb-init_1.2.0_amd64.deb /tmp/dumb-init_1.2.0_amd64.deb

RUN \
    apt-get update \
    && apt-get install -y gnupg2 curl \
    && curl -fsSL https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list \
    && apt-get update \
    && apt-get install --no-install-recommends -y google-chrome-stable \
    && rm -rf /var/lib/apt/lists/* \
    && dpkg -i /tmp/dumb-init_1.2.0_amd64.deb \
    && rm /tmp/dumb-init_1.2.0_amd64.deb \
    && groupadd -r chrome \
    && useradd -rmg chrome -G audio,video chrome

USER chrome
CMD ["google-chrome"] 
ENTRYPOINT ["dumb-init", "--"]

