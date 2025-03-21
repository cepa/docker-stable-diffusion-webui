FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

# Prerequisites
RUN apt-get update && apt-get install -y \
    software-properties-common \
    locales \
    git \
    wget

# Python 3.11
RUN add-apt-repository ppa:deadsnakes/ppa && apt-get update && apt-get install -y \
    python3.11 \
    python3.11-venv \
    libgl1 \
    libglib2.0-0
RUN cd /usr/bin \
    && unlink python3 \
    && ln -s python3.11 python3

# Get Stable Diffusion WebUI from AUTOMATIC1111
RUN mkdir -p /srv && cd /srv && git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui
RUN useradd -m -d /srv/stable-diffusion-webui -s /bin/bash stable
RUN chown -R stable:stable /srv/stable-diffusion-webui

WORKDIR /srv/stable-diffusion-webui
VOLUME /srv/stable-diffusion-webui/models
VOLUME /srv/stable-diffusion-webui/outputs

USER stable

# Install
RUN ./webui.sh --exit --skip-torch-cuda-test

# Entrypoint
CMD ./webui.sh --listen
