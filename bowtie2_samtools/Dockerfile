FROM ubuntu:18.04
#ARG UBUNTU_VERSION=18.04
#FROM rocker/rstudio

LABEL maintainer="Andres Quintero andres.quintero@bioquant.uni-heidelberg.de"


# See http://bugs.python.org/issue19846
ENV LANG C.UTF-8

RUN apt-get update && apt-get install -y \
    unzip \
    wget \
    gcc \
    g++ \
    libtbb-dev


RUN wget https://downloads.sourceforge.net/project/bowtie-bio/bowtie2/2.3.2/bowtie2-2.3.2-linux-x86_64.zip
RUN unzip bowtie2-2.3.2-linux-x86_64.zip && \
    rm -rf bowtie2-2.3.2-linux-x86_64.zip \
    mv bowtie2-2.4.1-linux-x86_64/* /usr/local/bin/ 

