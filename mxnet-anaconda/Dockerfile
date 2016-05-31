FROM nvidia/cuda:7.5-cudnn4-devel
MAINTAINER Liu Siyuan <SLIU019@e.ntu.edu.sg>

# Install some dependencies and common utils
RUN apt-get update && apt-get install -y build-essential git libatlas-base-dev libopencv-dev
RUN apt-get install -y wget unzip

# Download MXNet and install it
WORKDIR /root
RUN git clone --recursive https://github.com/dmlc/mxnet
ADD config.mk /root/mxnet/config.mk

WORKDIR /root/mxnet
RUN make -j$(nproc)

# Set anaconda path
ENV ANACONDA /opt/anaconda
ENV PATH $ANACONDA/bin:$PATH

# Download anaconda and install it
RUN wget http://repo.continuum.io/archive/Anaconda2-4.0.0-Linux-x86_64.sh -P /tmp
RUN bash /tmp/Anaconda2-4.0.0-Linux-x86_64.sh -b -p $ANACONDA
RUN rm /tmp/Anaconda2-4.0.0-Linux-x86_64.sh

# Copy the config file into docker
RUN jupyter notebook --generate-config && ipython profile create
ADD jupyter_notebook_config.py  /root/.jupyter
ADD matplotlib_init.py /root/.ipython/profile_default/startup

# Add Tini
ENV TINI_VERSION v0.9.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /tini
RUN chmod +x /tini
ENTRYPOINT ["/tini", "--"]

# Add Python support
WORKDIR /root/mxnet/python
RUN python setup.py install

# Change workdir
WORKDIR /root/workspace

# Default command is to run a jupyter notebook at 0.0.0.0:8888 in headless mode
CMD ["jupyter", "notebook"]
