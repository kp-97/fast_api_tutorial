FROM python:3.11-slim

RUN groupadd -g 10001 nonroot && \
    useradd -u 10000 -g nonroot -m -s /bin/bash nonroot

RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    tini \
    dnsutils \
    && rm -rf /var/lib/apt/lists/*
RUN pip install --upgrade pip

WORKDIR /app
RUN chown nonroot:nonroot /app
USER nonroot
COPY --chown=nonroot:nonroot . .

ENV PATH="/home/nonroot/.local/bin:${PATH}"