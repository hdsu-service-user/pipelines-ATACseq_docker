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
    rm -rf bowtie2-2.3.2-linux-x86_64.zip && \
    ls -l && \
    mv bowtie2-2.3.2/* /usr/local/bin/ 
#    mkdir /usr/local/bin/ && \



RUN mkdir /genomeData && \
    cd /genomeData && \
    wget http://igenomes.illumina.com.s3-website-us-east-1.amazonaws.com/Homo_sapiens/UCSC/hg38/Homo_sapiens_UCSC_hg38.tar.gz && \
    for f in *.tar.gz; do tar -zxvf "$f"; done



##http://igenomes.illumina.com.s3-website-us-east-1.amazonaws.com/Homo_sapiens/UCSC/hg19/Homo_sapiens_UCSC_hg19.tar.gz
#https://s3.amazonaws.com/local-run-manager/genomes/Homo_sapiens.zip
##https://s3.amazonaws.com/local-run-manager/genomes/Homo_sapiens_hg19.zip
