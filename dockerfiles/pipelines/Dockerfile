# Builds a Docker image with the necessary libraries for the Bitbucket
# Pipeline tests of FEniCS components (excluding DOLFIN).  The image
# is at:
#
#    https://quay.io/repository/fenicsproject/pipelines
#
# Authors:
# Garth N. Wells <gnw20@cam.ac.uk>

FROM ubuntu:16.04
MAINTAINER fenics-project <fenics-support@googlegroups.org>

USER root
WORKDIR /tmp

# Non-Python utilities and libraries
RUN apt-get -qq update && \
    apt-get -y --with-new-pkgs \
        -o Dpkg::Options::="--force-confold" upgrade && \
    apt-get -y install \
        cmake \
        g++ \
        git \
        libmpich-dev \
        mpich \
        wget && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Install Python3 based environment
RUN apt-get -qq update && \
    apt-get -y --with-new-pkgs \
        -o Dpkg::Options::="--force-confold" upgrade && \
    apt-get -y install \
        python3-dev \
        python3-minimal \
        python3-numpy \
        python3-pytest \
        python3-pytest-cov \
        python3-wheel &&  \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Install setuptools
RUN wget https://bootstrap.pypa.io/get-pip.py && \
    python3 get-pip.py && \
    pip3 install --no-cache-dir setuptools && \
    rm -rf /tmp/*

# Pip install of packages
RUN pip3 install --no-cache-dir sympy && \
    pip3 install --no-cache-dir mpi4py && \
    pip3 install --no-cache-dir flake8 && \
    rm -rf /tmp/*
