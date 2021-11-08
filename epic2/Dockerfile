FROM ubuntu:18.04

LABEL maintainer="Andres Quintero andres.quintero@bioquant.uni-heidelberg.de"



ARG USE_PYTHON_3_NOT_2=True
ARG _PY_SUFFIX=${USE_PYTHON_3_NOT_2:+3}
ARG PYTHON=python${_PY_SUFFIX}
ARG PIP=pip${_PY_SUFFIX}


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


RUN apt-get update && apt-get install -y \
    ${PYTHON} \
    ${PYTHON}-pip

RUN ${PIP} --no-cache-dir install --upgrade \
    pip \
    setuptools

# Some TF tools expect a "python" binary
RUN ln -s $(which ${PYTHON}) /usr/local/bin/python 


# Install macs2
RUN ${PIP} install Cython
RUN ${PIP} install pysam
RUN ${PIP} install epic2
