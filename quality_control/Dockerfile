FROM rocker/tidyverse
#FROM rocker/rstudio

LABEL maintainer="Andres Quintero andres.quintero@bioquant.uni-heidelberg.de"

# from the tensorflow dockerfile: 
# https://github.com/tensorflow/tensorflow/blob/master/tensorflow/tools/dockerfiles/dockerfiles/cpu-jupyter.Dockerfile

ARG PYTHON=python3
ARG PIP=pip3


# See http://bugs.python.org/issue19846
ENV LANG C.UTF-8

RUN apt-get update && apt-get install -y \
    build-essential \
    wget \
    gcc \
    g++ \
    libtbb-dev \
    libncurses5-dev \
    libncursesw5-dev \
    zlib1g-dev \
    libcurl4-openssl-dev \
    libjpeg-dev \
    libbz2-dev \
    liblzma-dev \
    libxtst6 \
    libxext6 \
    libsm6 \
    libglib2.0-0 \
    libxrender-dev \
    libfontconfig1 \
    tcl8.6-dev \
    tk8.6-dev
    

    


RUN apt-get update && apt-get install -y \
    ${PYTHON} \
    ${PYTHON}-pip

RUN ${PIP} --no-cache-dir install --upgrade \
    pip \
    setuptools

# Some TF tools expect a "python" binary
RUN ln -s $(which ${PYTHON}) /usr/local/bin/python 


# RUN ${PIP} install tensorflow==2.2.0


RUN R -e "install.packages('cowplot')"


# Install samtools
RUN wget https://github.com/samtools/samtools/releases/download/1.10/samtools-1.10.tar.bz2 && \
    tar -jxvf samtools-1.10.tar.bz2 && \
    cd samtools-1.10 && \
    ./configure --prefix=/usr/local/ && \
    make && \
    make install



