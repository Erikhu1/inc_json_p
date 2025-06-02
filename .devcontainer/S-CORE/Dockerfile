# Set the base image with a default version
ARG BASE_IMAGE=debian:12
FROM ${BASE_IMAGE} AS builder

# Set noninteractive env for apt-get to avoid prompts
ENV DEBIAN_FRONTEND=noninteractive

# Define arguments for versions
ARG GCC_VERSION=11.3.0-12
ARG LLVM_VERSION=16.0.6-15

# Update package list and install dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    wget git git-lfs graphviz default-jre libtinfo5 g++-${GCC_VERSION} gdb googletest gcovr cmake \
    clang-${LLVM_VERSION} clang-tidy-${LLVM_VERSION} clang-format-${LLVM_VERSION} doxygen && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Specify default versions via update alternatives
RUN update-alternatives --install /usr/bin/clang-tidy clang-tidy /usr/bin/clang-tidy-${LLVM_VERSION} 100 && \
    update-alternatives --set clang-tidy /usr/bin/clang-tidy-${LLVM_VERSION} && \
    update-alternatives --install /usr/bin/clang-format clang-format /usr/bin/clang-format-${LLVM_VERSION} 100 && \
    update-alternatives --set clang-format /usr/bin/clang-format-${LLVM_VERSION} && \
    update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-${GCC_VERSION} 100 && \
    update-alternatives --set g++ /usr/bin/g++-${GCC_VERSION}

# Install bazelisk tool
RUN wget https://github.com/bazelbuild/bazelisk/releases/download/v1.26.0/bazelisk-linux-amd64 && \
    chmod +x bazelisk-linux-amd64 && \
    mv bazelisk-linux-amd64 /usr/local/bin/bazel
