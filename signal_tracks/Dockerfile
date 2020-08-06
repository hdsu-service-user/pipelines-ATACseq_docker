FROM ubuntu:18.04
#ARG UBUNTU_VERSION=18.04
#FROM rocker/rstudio

LABEL maintainer="Andres Quintero andres.quintero@bioquant.uni-heidelberg.de"


# See http://bugs.python.org/issue19846
ENV LANG C.UTF-8

RUN apt-get update && apt-get install -y \
    build-essential \
    unzip \
    wget \
    gcc \
    g++ \
    libtbb-dev \
    libncurses5-dev \
    libncursesw5-dev \
    libjpeg-dev \
    libbz2-dev \
    liblzma-dev \
    zlib1g-dev \
    libcurl4-openssl-dev

RUN wget https://github.com/samtools/samtools/releases/download/1.10/samtools-1.10.tar.bz2 && \
    tar -jxvf samtools-1.10.tar.bz2 && \
    cd samtools-1.10 && \
    ./configure --prefix=/usr/local/ && \
    make && \
    make install


RUN wget https://github.com/arq5x/bedtools2/releases/download/v2.29.2/bedtools.static.binary && \
    mv bedtools.static.binary /usr/local/bin/bedtools  && \
    chmod 555 /usr/local/bin/bedtools


