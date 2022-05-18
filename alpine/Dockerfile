FROM alpine:3.15.4
ARG VERSION=3.12.5

RUN apk add wget dpkg iptables iproute2 procps ca-certificates libxml2 libidn2 zlib bash libc6-compat && \
    dpkg --add-architecture amd64 && \
    wget -q -O /tmp/nordvpn.deb https://repo.nordvpn.com/deb/nordvpn/debian/pool/main/nordvpn_${VERSION}_amd64.deb && \
    dpkg --install --force-depends /tmp/nordvpn.deb && \
    mkdir -p /run/nordvpn

#ENTRYPOINT ["/usr/bin/nordvpnd", "&"]
ENTRYPOINT ["tail", "-f", "/dev/null"]
