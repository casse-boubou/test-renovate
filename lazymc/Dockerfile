ARG ALPINE_BASE_IMAGE_VERSION="3.23"
####################
# BUILD LAZYMC
####################
FROM alpine:${ALPINE_BASE_IMAGE_VERSION} AS builder
# Update index, install app
ARG LAZYMC_VERSION="v0.2.10"
RUN echo "Installing base packages" \
    && apk --update --no-cache add \
    cargo=1.91.1-r0 \
    git=2.52.0-r0
RUN wget -q --no-verbose https://github.com/timvisee/lazymc/archive/refs/tags/${LAZYMC_VERSION}.zip && \
    unzip ${LAZYMC_VERSION}.zip -q -d lazymc-${LAZYMC_VERSION} && \
    mv lazymc-${LAZYMC_VERSION}/lazymc-* lazymc
WORKDIR /lazymc
RUN cargo build --release

