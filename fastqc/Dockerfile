FROM ubuntu:18.04
#ARG UBUNTU_VERSION=18.04


LABEL maintainer="Andres Quintero andres.quintero@bioquant.uni-heidelberg.de"

RUN apt-get update && apt-get install -y \
    locales locales-all
RUN touch /etc/default/locale && \
    echo LANGUAGE=en_US.UTF-8 >> /etc/default/locale && \
    echo LANG=en_US.UTF-8 >> /etc/default/locale && \
    echo LC_ALL=en_US.UTF-8 >> /etc/default/locale && \
    locale-gen en_US.UTF-8 && \
    dpkg-reconfigure locales
ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8

RUN apt-get update && apt-get install -y \
    libjpeg-dev \
    libbz2-dev \
    liblzma-dev \
    zlib1g-dev \
    libcurl4-openssl-dev\
    unzip \
    wget \
    default-jre

RUN apt-get update && apt-get install -y \
    libfindbin-libs-perl

RUN wget https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v0.11.9.zip && \
    unzip fastqc_v0.11.9.zip && \
    rm -rf fastqc_v0.11.9.zip && \
    ls -l FastQC && \
    chmod 755 /FastQC/fastqc && \
    ln -s /FastQC/fastqc /usr/local/bin/fastqc
    

