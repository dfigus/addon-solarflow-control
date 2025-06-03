ARG BUILD_FROM

FROM alpine:3.22 AS builder
############## builder ##############

ARG SOLARFLOW_RELEASE="0.77"
ARG SOLARFLOW_FORK_RELEASE="0.79b2"
ARG SOLARFLOW_BT_DIGEST="f6c838dd381c6a2a7adf58f2a638601388702c89"


RUN \
    echo "**** install build packages ****" && \
    apk update && \
    apk add --no-cache git

RUN \
    git clone https://github.com/reinhard-brandstaedter/solarflow-control /tmp/solarflow && \
    cd /tmp/solarflow && \
    git checkout "${SOLARFLOW_RELEASE}"

    RUN \
    git clone https://github.com/dfigus/solarflow-control /tmp/solarflow_fork && \
    cd /tmp/solarflow_fork && \
    git checkout "${SOLARFLOW_FORK_RELEASE}"

RUN \
    git clone https://github.com/reinhard-brandstaedter/solarflow-bt-manager /tmp/solarflow-bt && \
    cd /tmp/solarflow-bt && \
    git checkout "${SOLARFLOW_BT_DIGEST}"


####### runtime ###########
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

COPY --from=builder /tmp/solarflow/src/solarflow /solarflow
COPY --from=builder /tmp/solarflow_fork/src/solarflow /solarflow_fork
COPY --from=builder /tmp/solarflow/src/requirements.txt /tmp/requirements.txt
COPY --from=builder /tmp/solarflow-bt/src/ /solarflow-bt

RUN pip3 install --no-cache-dir -Ur /tmp/requirements.txt
#RUN pip3 install --no-cache-dir -Ur /solarflow-bt/requirements.txt

# Copy root filesystem
COPY rootfs /

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_DESCRIPTION
ARG BUILD_NAME
ARG BUILD_REF
ARG BUILD_REPOSITORY
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="${BUILD_NAME}" \
    io.hass.description="${BUILD_DESCRIPTION}" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Daniel Figus <10271668+dfigus@users.noreply.github.com>" \
    org.opencontainers.image.title="${BUILD_NAME}" \
    org.opencontainers.image.description="${BUILD_DESCRIPTION}" \
    org.opencontainers.image.vendor="dfigus" \
    org.opencontainers.image.authors="Daniel Figus <10271668+dfigus@users.noreply.github.com>" \
    org.opencontainers.image.licenses="MIT" \
    org.opencontainers.image.url="https://github.com/dfigus/addon-solarflow-control" \
    org.opencontainers.image.source="https://github.com/${BUILD_REPOSITORY}" \
    org.opencontainers.image.documentation="https://github.com/${BUILD_REPOSITORY}/blob/main/README.md" \
    org.opencontainers.image.created=${BUILD_DATE} \
    org.opencontainers.image.revision=${BUILD_REF} \
    org.opencontainers.image.version=${BUILD_VERSION}
