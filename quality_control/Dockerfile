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
    libjpeg-dev \
    libbz2-dev \
    liblzma-dev \
    libxtst6:i386
    #libxtst6
    


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


