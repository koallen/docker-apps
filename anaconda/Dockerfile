FROM ubuntu:14.04
MAINTAINER Liu Siyuan <SLIU019@e.ntu.edu.sg>

ENV ANACONDA /opt/anaconda
ENV PATH $ANACONDA/bin:$PATH

RUN apt-get update && apt-get install -y wget
RUN wget http://repo.continuum.io/archive/Anaconda2-4.0.0-Linux-x86_64.sh -P /tmp
RUN bash /tmp/Anaconda2-4.0.0-Linux-x86_64.sh -b -p $ANACONDA
RUN rm /tmp/Anaconda2-4.0.0-Linux-x86_64.sh

WORKDIR /root

CMD ["jupyter", "notebook"]
