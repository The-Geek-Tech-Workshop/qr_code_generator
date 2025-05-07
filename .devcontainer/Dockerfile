# Use the latest Ubuntu image as the base
FROM ubuntu:latest

# Set Flutter version as a build argument
ARG FLUTTER_VERSION=3.29.3-stable

# Install required dependencies
RUN apt-get update && apt-get install -y \
    curl \
    git \
    unzip \
    xz-utils \
    libglu1-mesa \
    ca-certificates \
    && apt-get clean

# Install Flutter (stable release) using the specified version
RUN curl -LO https://storage.googleapis.com/flutter_infra_release/releases/stable/linux/flutter_linux_${FLUTTER_VERSION}.tar.xz \
    && tar xf flutter_linux_${FLUTTER_VERSION}.tar.xz -C /usr/local \
    && rm flutter_linux_${FLUTTER_VERSION}.tar.xz

# Add Flutter to PATH
ENV PATH="/usr/local/flutter/bin:/usr/local/flutter/bin/cache/dart-sdk/bin:${PATH}"

# Set the working directory
WORKDIR /workspace

# Run Flutter doctor to pre-cache dependencies
# RUN flutter doctor --android-licenses || true && flutter doctor
