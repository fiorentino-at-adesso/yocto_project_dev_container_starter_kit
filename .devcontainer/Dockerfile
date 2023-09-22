FROM ubuntu:20.04

# Defines
ARG USER=builder
ARG USER_ID=1000
ARG GROUP_ID=1000

ENV DEBIAN_FRONTEND=noninteractive

# Intended command for the image
CMD "/bin/bash"
SHELL ["/bin/bash", "-c"]

RUN id -g $USER 2>/dev/null || groupadd -g $GROUP_ID $USER
RUN id $USER 2>/dev/null || useradd --uid $USER_ID --gid $GROUP_ID --create-home $USER
RUN echo $USER" ALL=(ALL) NOPASSWD: ALL" | tee -a /etc/sudoers

# Set the locale
RUN apt-get update && \
    apt-get install -y locales && \
    rm -rf /var/lib/apt/lists/*
RUN locale-gen en_US.UTF-8
ENV LANG='en_US.UTF-8'
ENV LANGUAGE='en_US:en'
ENV LC_ALL='en_US.UTF-8'

# Install dependencies
RUN apt-get update \
    && apt-get install -y \
        python2 \
        python3 \
        python3-pip \
        python-is-python3 \
        locales \
        git \
        chrpath \
        cpio \
        diffstat \
        gawk \
        wget \
        zstd \
        lz4 \
        libglib2.0-dev \
        parted \
        mtools \
        libssl-dev \
        libcrypto++-dev \
    && rm -rf /var/lib/apt/lists/*

RUN echo "export LANG='en_US.UTF-8'" >> /home/$USER/.bashrc
RUN echo "export LANGUAGE='en_US:en'" >> /home/$USER/.bashrc
RUN echo "export LC_ALL='en_US.UTF-8'" >> /home/$USER/.bashrc
RUN update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8

# Initial setup when you login
USER $USER
