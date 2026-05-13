FROM python:3.11-slim

# Create non-root user
RUN groupadd -g 10001 nonroot && \
    useradd -u 10000 -g nonroot -m -s /bin/bash nonroot

# Install system dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl git curl tini \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# Set ownership early
RUN chown nonroot:nonroot /app
USER nonroot

# Add local bin to PATH
ENV PATH="/home/nonroot/.local/bin:${PATH}"

# Install dependencies
COPY --chown=nonroot:nonroot pyproject.toml .
# Use --no-cache-dir to keep the image slim
RUN pip install --user --no-cache-dir .

# Copy source code
COPY --chown=nonroot:nonroot . .

# Finalize install (if your pyproject.toml defines scripts/entrypoints)
RUN pip install --user --no-cache-dir .

# Use tini to handle signals (like Ctrl+C) properly
ENTRYPOINT ["/usr/bin/tini", "--"]

# Run uvicorn
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]