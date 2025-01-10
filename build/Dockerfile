
ARG CUDA_VERSION
ARG CUDA_DISTR
ARG CUDA_OS_VERSION
FROM nvidia/cuda:$CUDA_VERSION-$CUDA_DISTR-$CUDA_OS_VERSION

# setup ubuntu
RUN apt-get update \
    && apt-get install -y locales \
    && rm -rf /var/lib/apt/lists/* \
	&& localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8
ENV LANG=en_US.utf8

## Prepare setup base dependencies
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get update -qq \
    && apt upgrade -y \
    && apt-get install -y --no-install-recommends \
        apt-utils \
        build-essential \
        htop \
        curl \
        unzip \
        vim \
        wget 

## Prepare setup of R and Python dependencies
RUN apt-get install -y --no-install-recommends \
        cmake \
        curl \
        git \
        gnupg2 \
        htop \
        lsb-release \
        libcairo2-dev \
        libcurl4-openssl-dev \
        libgdbm-dev \
        libncurses5-dev \
        libnss3-dev \
        libssl-dev \
        libxml2-dev \
        meson \
        ninja-build \
        nvidia-cuda-toolkit \
        python3 \
        python3-pip \
        python3-setuptools \
        zlib1g-dev

RUN apt purge --auto-remove cmake -y \
    && wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null | gpg --dearmor - | tee /usr/share/keyrings/kitware-archive-keyring.gpg >/dev/null \
    && echo 'deb [signed-by=/usr/share/keyrings/kitware-archive-keyring.gpg] https://apt.kitware.com/ubuntu/ jammy main' | tee /etc/apt/sources.list.d/kitware.list >/dev/null \
    && apt update \
    && apt install -y \
        cmake \
        cmake-curses-gui

RUN apt install -y \
        libfontconfig1 \
        libgit2-dev \
        python3-dev \
    && apt-get update \
    && apt upgrade -y \
    && apt autoremove -y \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
