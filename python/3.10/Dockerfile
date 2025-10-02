FROM python:3.10.15-slim-bookworm

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends \
    libblas-dev \
    liblapack-dev \
    gfortran \
    g++ \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

ENV LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libjemalloc.so

RUN groupadd -g 10000 -r app && \
    useradd --no-log-init -r -g 10000 -u 10000 app && \
    mkdir -p /home/app && \
    chown app:app /home/app

USER app
