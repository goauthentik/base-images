ARG BUILD_IMAGE=ghcr.io/goauthentik/fips-debian:trixie-slim-fips

FROM ${BUILD_IMAGE} AS builder

RUN --mount=type=bind,target=/tmp/geoip.sh,src=./geoip.sh \
    apt-get update && \
    apt-get install -y wget && \
    sh /tmp/geoip.sh /geoip "${GEOIP_MONTH}"

FROM scratch

COPY --from=builder /geoip /geoip
