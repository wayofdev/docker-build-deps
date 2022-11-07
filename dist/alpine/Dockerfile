# Auto-generated via Ansible: edit src/Dockerfiles/all/Dockerfile.j2 instead.

FROM atkrad/wait4x:latest as wait4x

FROM docker:20.10.21

# Labels
# https://github.com/opencontainers/image-spec/blob/main/annotations.md
LABEL "maintainer"="lotyp <lotyp7@gmail.com>"
LABEL "vendor"="wayofdev"
LABEL "org.opencontainers.image.authors"="lotyp <lotyp7@gmail.com>"
LABEL "org.opencontainers.image.url"="https://hub.docker.com/r/wayofdev/build-deps"
LABEL "org.opencontainers.image.documentation"="https://github.com/wayofdev/docker-build-deps"
LABEL "org.opencontainers.image.source"="https://github.com/wayofdev/docker-build-deps"
LABEL "org.opencontainers.image.vendor"="wayofdev"
LABEL "org.opencontainers.image.licenses"="MIT"
LABEL "org.opencontainers.image.ref.name"="alpine"
LABEL "org.opencontainers.image.title"="build-deps-alpine"
LABEL "org.opencontainers.image.description"="build-deps-alpine"

ENV LANG="en_US.UTF-8"
ENV LC_ALL="en_US.UTF-8"
ENV LANGUAGE="en_US.UTF-8"

ENV GOSS_VER=v0.3.20
ENV GOSS_FILES_STRATEGY=cp

ARG TARGETPLATFORM

COPY --from=wait4x /usr/bin/wait4x /usr/local/bin/wait4x

RUN set -eux; \
    apk -U upgrade -a \
    && apk add --no-cache \
        git \
        bash \
        unzip \
        nano \
        ca-certificates \
        tzdata \
        curl \
        gettext \
        make \
        tar \
        bzip2 \
        net-tools \
    && if [ "$TARGETPLATFORM" = "linux/amd64" ]; then ARCHITECTURE=amd64; elif [ "$TARGETPLATFORM" = "linux/arm/v7" ]; then ARCHITECTURE=arm; elif [ "$TARGETPLATFORM" = "linux/arm64" ]; then ARCHITECTURE=arm64; else ARCHITECTURE=amd64; fi \
    && curl -L "https://github.com/FiloSottile/mkcert/releases/download/v1.4.4/mkcert-v1.4.4-linux-${ARCHITECTURE}" -o /usr/local/bin/mkcert \
    && chmod +x /usr/local/bin/mkcert \
    && curl -fsSL https://goss.rocks/install | sh \
    && cd /tmp \
    && curl -sSLO https://raw.githubusercontent.com/aelsabbahy/goss/master/extras/dcgoss/dcgoss \
    && mv dcgoss /usr/local/bin \
    && chmod +x /usr/local/bin/dcgoss \
    && addgroup -g 1000 wod \
    && adduser -u 1000 wod -D -h /home/wod -s /bin/bash -G wod

WORKDIR /home/wod

ENTRYPOINT []

CMD ["/bin/bash"]
