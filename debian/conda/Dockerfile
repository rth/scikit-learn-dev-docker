FROM amd64/debian:unstable

RUN apt-get update && apt-get install -y gcc g++ git make wget bzip2

RUN wget http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda.sh && \
    chmod +x miniconda.sh && \
    ./miniconda.sh -b

ENV PATH "/root/miniconda3/bin/:${PATH}"

RUN conda update -y conda

RUN conda create -n sklearn-env numpy scipy cython pytest nose docutils python=3.6

# switch from dash to bash to make "source activate" work
RUN echo "dash dash/sh boolean false" | debconf-set-selections && \
    DEBIAN_FRONTEND=noninteractive dpkg-reconfigure dash 

RUN conda activate sklearn-env && \
    git clone https://github.com/scikit-learn/scikit-learn.git && \
    cd scikit-learn && git checkout master

RUN make

RUN pytest sklearn
