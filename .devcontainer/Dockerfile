# Use Miniconda3 base image
FROM continuumio/miniconda3:latest

# Set working directory (this will be mounted by the devcontainer)
WORKDIR /workspace

# Avoid interactive prompts
ENV DEBIAN_FRONTEND=noninteractive

# Install system dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    curl \
    git \
    ca-certificates \
    libglib2.0-0 \
    libsm6 \
    libxrender1 \
    libxext6 \
    libgl1-mesa-glx \
    && rm -rf /var/lib/apt/lists/*

# Install Node.js 20
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - \
    && apt-get install -y nodejs \
    && rm -rf /var/lib/apt/lists/*

# Update conda
RUN conda update -n base -c defaults conda -y

# Use the dev environment for all subsequent RUN commands
SHELL ["conda", "run", "-n", "dev", "/bin/bash", "-c"]

# Default command to keep container alive
CMD ["sleep", "infinity"]