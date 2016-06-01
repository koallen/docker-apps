FROM koallen/anaconda-cuda
MAINTAINER Liu Siyuan <SLIU019@e.ntu.edu.sg>

# Install dependencies
RUN apt-get install -y git libprotobuf-dev libopencv-dev libhdf5-serial-dev protobuf-compiler libatlas-base-dev libleveldb-dev libsnappy-dev
RUN apt-get install -y --no-install-recommends libboost-all-dev
RUN apt-get install -y libgflags-dev libgoogle-glog-dev liblmdb-dev

# Set environment variables
ENV LD_LIBRARY_PATH /opt/anaconda/lib:$LD_LIBRARY_PATH
ENV PYTHONPATH /root/caffe/python:$PYTHONPATH

# Download Caffe
WORKDIR /root
RUN git clone https://github.com/BVLC/caffe.git

# Compile Caffe
WORKDIR /root/caffe
ADD Makefile.config /root/caffe/Makefile.config
RUN make all -j$(nproc)

# Add Python support
WORKDIR /root/caffe/python
RUN for req in $(cat requirements.txt); do pip install $req; done
WORKDIR /root/caffe
RUN make pycaffe -j$(nproc)

# Change workdir
WORKDIR /root/workspace
