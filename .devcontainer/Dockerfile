FROM ubuntu:22.04

# Create vscode user before installing stuff
RUN groupadd --gid 1000 vscode && \
    useradd -s /bin/bash --uid 1000 --gid vscode -m vscode

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
    apt-transport-https

# Add Bazel apt repo and install Bazel
RUN curl -fsSL https://bazel.build/bazel-release.pub.gpg | gpg --dearmor >bazel.gpg && \
    mv bazel.gpg /etc/apt/trusted.gpg.d/ && \
    echo "deb [arch=amd64] https://storage.googleapis.com/bazel-apt stable jdk1.8" | tee /etc/apt/sources.list.d/bazel.list && \
    apt-get update && \
    apt-get install -y bazel

# Set default user
USER vscode

WORKDIR /workspaces/practice_bazel
