FROM ubuntu:bionic

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
  && apt-get install -y \
    mpich \
    python3 \
    python3-pip \
    python3-tk \
    python3-opengl \
  && rm -rf /var/lib/apt/lists/*

COPY . /spinningup/
WORKDIR /spinningup/
RUN python3 -m pip install --upgrade pip
RUN python3 -m pip install tensorflow==1.8
RUN python3 -m pip install torch==1.3.1
RUN python3 -m pip install -e .
