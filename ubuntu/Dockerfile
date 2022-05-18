FROM ubuntu:22.04
ARG VERSION=3.12.5

RUN mkdir -p /run/nordvpn && \
    apt update && \
    apt install -y wget && \
    wget -O /tmp/nordrepo.deb https://repo.nordvpn.com/deb/nordvpn/debian/pool/main/nordvpn-release_1.0.0_all.deb && \
    apt install -y /tmp/nordrepo.deb && \
    apt update && \
    apt install -y nordvpn=$VERSION && \
    apt remove -y wget nordvpn-release && \
    rm -f /tmp/nordrepo.deb && \
    usermod -aG nordvpn root

ENTRYPOINT ["/usr/sbin/nordvpnd", "&"]
