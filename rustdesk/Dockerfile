ARG BUILD_FROM=ghcr.io/hassio-addons/base:21.0.1
# https://github.com/hassio-addons/addon-base/releases
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

# https://github.com/rustdesk/rustdesk-server/releases
ARG BUILD_ARCH
ARG RUSTDESK_SERVER_VERSION="1.1.15"

# Add Rustdesk-Server
RUN set -eux \
    apk update; \
    \
    apk add --no-cache --virtual .build-deps \
        unzip=6.0-r15 \
        ; \
    mkdir -p /opt; \
    if [ "${BUILD_ARCH}" = "aarch64" ]; then ARCH="arm64v8"; \
    elif [ "${BUILD_ARCH}" = "amd64" ]; then ARCH="amd64"; \
    fi; \
    curl -S -J -L -o /tmp/rustdesk-server.zip \
        "https://github.com/rustdesk/rustdesk-server/releases/download/${RUSTDESK_SERVER_VERSION}/rustdesk-server-linux-${ARCH}.zip"; \
    unzip /tmp/rustdesk-server.zip -d /opt; \
    mv /opt/${ARCH} /opt/rustdesk-server; \
    rm /tmp/rustdesk-server.zip; \
    apk del .build-deps
