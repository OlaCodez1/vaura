# Base image with common dev tools
FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Install Flutter dependencies
RUN apt-get update && apt-get install -y \
    curl unzip git xz-utils libglu1-mesa \
    && rm -rf /var/lib/apt/lists/*

# Install Flutter
ENV FLUTTER_VERSION=3.22.0
ENV FLUTTER_HOME=/opt/flutter
RUN git clone https://github.com/flutter/flutter.git -b stable $FLUTTER_HOME
ENV PATH="${FLUTTER_HOME}/bin:${FLUTTER_HOME}/bin/cache/dart-sdk/bin:${PATH}"

# Pre-cache to speed up dev startup
RUN flutter precache

# Accept Android licenses (optional, only if using Android tools later)
RUN yes | flutter doctor --android-licenses || true
