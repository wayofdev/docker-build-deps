FROM jwilder/dockerize:0.6.1 as dockerize

FROM %%DOCKER_IMAGE%%

LABEL maintainer="arturs.terehovics@moneliq.com" \
    vendor="Moneliq"

ENV LANG="en_US.UTF-8"
ENV LC_ALL="en_US.UTF-8"
ENV LANGUAGE="en_US.UTF-8"

ENV GOSS_FILES_STRATEGY=cp

ARG ALPINE_VERSION=3.13

COPY --from=dockerize /usr/local/bin/dockerize /usr/local/bin/dockerize

RUN set -eux; \
    rm -f /etc/apk/repositories &&\
    echo "http://dl-cdn.alpinelinux.org/alpine/v${ALPINE_VERSION}/main" >> /etc/apk/repositories && \
    echo "http://dl-cdn.alpinelinux.org/alpine/v${ALPINE_VERSION}/community" >> /etc/apk/repositories

RUN addgroup -g 8385 wod && adduser -u 8385 wod -D -h /home/wod -s /bin/sh -G wod

RUN set -eux; \
    apk add --update --no-cache \
        curl \
        bash \
        && curl -fsSL https://goss.rocks/install | sh \
        && cd /tmp \
        && curl -sSLO https://raw.githubusercontent.com/aelsabbahy/goss/master/extras/dcgoss/dcgoss \
        && mv dcgoss /usr/local/bin \
        && chmod +x /usr/local/bin/dcgoss

WORKDIR /home/wod

ENTRYPOINT []
CMD ["/bin/sh"]

RUN apk add --no-cache \
    gettext \
    build-base \
    make \
    wget \
    git \
    tar \
    gzip \
    unzip \
    bzip2 \
    gnupg \
    net-tools

USER wod
