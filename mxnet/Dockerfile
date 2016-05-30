FROM nvidia/cuda:7.5-cudnn4-devel
MAINTAINER Liu Siyuan <SLIU019@e.ntu.edu.sg>

# Install some dependencies and common utils
RUN apt-get update && apt-get install -y build-essential git libatlas-base-dev libopencv-dev
RUN apt-get install -y wget unzip

# Download MXNet and install it
WORKDIR /root
RUN git clone --recursive https://github.com/dmlc/mxnet

WORKDIR /root/mxnet
RUN make -j$(nproc)

# Add Python support
WORKDIR /root/mxnet/python
RUN apt-get install -y python-numpy python-setuptools
RUN python setup.py install
