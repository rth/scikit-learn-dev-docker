FROM amd64/debian:unstable

RUN apt-get update && apt-get install -y build-essential git make

RUN apt-get install -y python3 python3-scipy python3-numpy python3-setuptools python3-pkg-resources python3-pip

RUN git clone https://github.com/scikit-learn/scikit-learn.git && \
    cd scikit-learn && git checkout master

RUN pip3 install Cython nose pytest

RUN cd scikit-learn && pip3 install -e .

RUN pytest sklearn
