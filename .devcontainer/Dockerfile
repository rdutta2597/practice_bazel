FROM ubuntu:22.04

# Install Bazel dependencies
RUN apt-get update && apt-get install -y \
    curl \
    gnupg \
    openjdk-11-jdk \
    unzip \
    zip \
    git \
    wget \
    build-essential \
    bash \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

# Install Bazel
RUN apt-get update && \
    apt-get install -y apt-transport-https && \
    curl -fsSL https://bazel.build/bazel-release.pub.gpg | gpg --dearmor >bazel.gpg && \
    mv bazel.gpg /etc/apt/trusted.gpg.d/ && \
    echo "deb [arch=amd64] https://storage.googleapis.com/bazel-apt stable jdk1.8" | tee /etc/apt/sources.list.d/bazel.list && \
    apt-get update && \
    apt-get install -y bazel && \
    apt-get clean

# Set working directory
WORKDIR /workspaces/practice_bazel

