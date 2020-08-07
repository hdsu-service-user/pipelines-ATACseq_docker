FROM ubuntu:18.04
#ARG UBUNTU_VERSION=18.04
#FROM rocker/rstudio

LABEL maintainer="Andres Quintero andres.quintero@bioquant.uni-heidelberg.de"


# from the tensorflow dockerfile: 
# https://github.com/tensorflow/tensorflow/blob/master/tensorflow/tools/dockerfiles/dockerfiles/cpu-jupyter.Dockerfile

ARG USE_PYTHON_3_NOT_2=True
ARG _PY_SUFFIX=${USE_PYTHON_3_NOT_2:+3}
ARG PYTHON=python${_PY_SUFFIX}
ARG PIP=pip${_PY_SUFFIX}


# See http://bugs.python.org/issue19846

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
    wget \
    git \
    llvm \
    libboost-all-dev

RUN apt-get update && apt-get install -y \
    ${PYTHON} \
    ${PYTHON}-pip

RUN ${PIP} --no-cache-dir install --upgrade \
    pip \
    setuptools

# Some TF tools expect a "python" binary
RUN ln -s $(which ${PYTHON}) /usr/local/bin/python 


RUN ${PIP} install cython numpy scipy

ENV RGTDATA="/rgtdata"
RUN ${PIP} install RGT --no-binary RGT

#RUN git clone https://github.com/CostaLab/reg-gen.git
#RUN cd reg-gen; python setup.py install 
#RUN cd reg-gen; python setup.py install --prefix=/rgtdata

RUN cd /rgtdata && \
    find . -type d -exec chmod 777 {} \; && \
    find . -type f -exec chmod 666 {} \;
      
RUN ${PIP} install MOODS-python
#RUN cd /rgtdata ; python setupGenomicData.py --hg19
#RUN cd /rgtdata ; python setupGenomicData.py --hg38
#RUN cd ~/rgtdata ; python setupGenomicData.py --all

#RUN ${PIP} install tensorflow==2.2.0

# # Pick up some TF dependencies
# RUN apt-get update && apt-get install -y --no-install-recommends \
#         build-essential \
#         curl \
#         libfreetype6-dev \
#         libzmq3-dev \
#         pkg-config \
#         python \
#         python-dev \
#         rsync \
#         software-properties-common \
#         unzip \
#         && \
#     apt-get clean && \
#     rm -rf /var/lib/apt/lists/*

# RUN curl -O https://bootstrap.pypa.io/get-pip.py && \
#     python get-pip.py && \
#     rm get-pip.py
    

# RUN pip --no-cache-dir install \
#         ipykernel \
#         jupyter \
#         matplotlib \
#         numpy \
#        scipy \
#        tensorflow==2.0.0-alpha0 \
#         && \
#     python -m ipykernel.kernelspec

    
    
#docker build -t r_tensor2 .
#docker run -e PASSWORD=bratwurst -p 8787:8787 r_tensor2