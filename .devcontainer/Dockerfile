FROM python:3.11-slim

# 1. Setup User and System Dependencies
RUN groupadd -g 10001 nonroot && \
    useradd -u 10000 -g nonroot -m -s /bin/bash nonroot

RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    ssh \
    curl \
    tini \
    dnsutils \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --upgrade pip

WORKDIR /app
RUN chown nonroot:nonroot /app

# 2. Switch to nonroot user early
USER nonroot

# 3. Install Python dependencies (CACHED LAYER)
COPY --chown=nonroot:nonroot requirements.txt .
RUN pip install --user --no-cache-dir -r requirements.txt

# 4. Copy Application Code (NON-CACHED LAYER)
COPY --chown=nonroot:nonroot . .

ENV PATH="/home/nonroot/.local/bin:${PATH}"

# Default command to run your FastAPI app
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]