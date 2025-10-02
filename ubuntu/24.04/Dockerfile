FROM ubuntu:24.04

RUN apt-get update -y && \
    DEBIAN_FRONTEND=noninteractive apt-get upgrade -y && \
    DEBIAN_FRONTEND=noninteractive apt-get -y install --no-install-recommends binutils \
    ca-certificates \
    curl \
    htop \
    iproute2 \
    iputils-ping \
    lnav \
    lsof \
    net-tools && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN groupadd -r arkestro && \
    useradd --no-log-init -r -g arkestro arkuser && \
    mkdir -p /home/arkuser && \
    chown arkuser:arkestro /home/arkuser
