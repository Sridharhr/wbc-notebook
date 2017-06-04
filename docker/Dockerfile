#!/bin/bash
FROM jarvice/ubuntu-ibm-mldl-ppc64le
FROM python:2.7

#add Jupyter
RUN pip install notebook pyyaml

RUN apt-get update && apt-get install -y --no-install-recommends apt-utils
#add startupscripts
RUN apt-get install -y supervisor

RUN apt-get update && apt-get install -yq --no-install-recommends \
    git \
    vim \
    jed \
    emacs \
    build-essential \
    python-dev \
    unzip \
    libsm6 \
    pandoc \
    texlive-latex-base \
    texlive-latex-extra \
    texlive-fonts-extra \
    texlive-fonts-recommended \
    texlive-generic-recommended \
    libxrender1 \
    inkscape \
    && apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN apt-get update && \
        apt-get install -y --no-install-recommends libav-tools && \
        apt-get clean && \
        rm -rf /var/lib/apt/lists/*

RUN pip install numpy scipy
RUN pip install scikit-learn
RUN pip install pillow
RUN pip install h5py
RUN pip install --upgrade --no-deps git+git://github.com/Theano/Theano.git
RUN pip install keras

RUN apt-get update
RUN apt-get -y upgrade
RUN apt-get -y install build-essential cmake pkg-config
RUN apt-get -y install libjpeg8-dev libtiff5-dev libjasper-dev libpng12-dev
RUN apt-get -y install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
RUN apt-get -y install libxvidcore-dev libx264-dev
RUN apt-get -y install libgtk-3-dev
RUN apt-get -y install libatlas-base-dev gfortran
RUN apt-get -y install python2.7-dev python3.5-dev
RUN apt-get -y install python-opencv

WORKDIR /root
ADD startjupyter.sh /root/
ADD conf.d/* /etc/supervisor/conf.d/
ADD rc.local /etc/rc.local

#add wbc example 
WORKDIR /root
RUN git clone https://github.com/dhruvp/wbc-classification.git
