FROM python:3.12-slim-bookworm
ARG DD_GIT_REPOSITORY_URL
ARG DD_GIT_COMMIT_SHA

ENV DD_GIT_REPOSITORY_URL=${DD_GIT_REPOSITORY_URL}
ENV DD_GIT_COMMIT_SHA=${DD_GIT_COMMIT_SHA}

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

RUN pip install --upgrade pip && \
    pip install --no-cache-dir python-dotenv==1.1.1 ddtrace==3.15.0

USER app
