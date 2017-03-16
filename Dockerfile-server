FROM ppc64le/ubuntu:16.04

MAINTAINER Abhishek Dasgupta <abdasgupta@in.ibm.com>

RUN apt-get update && apt-get install -y \
        build-essential \
        curl \
        git \
        libfreetype6-dev \
        libpng12-dev \
        libzmq3-dev \
        pkg-config \
        python-dev \
        python-numpy \
        python-pip \
        software-properties-common \
        swig \
        zip \
        zlib1g-dev \
        libcurl3-dev \
        openjdk-8-jdk \
        openjdk-8-jre-headless \
        && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN curl -fSsL -O https://bootstrap.pypa.io/get-pip.py && \
    python get-pip.py && \
    rm get-pip.py

RUN pip install grpcio

COPY flowers-export/ /flowers-export/
COPY tensorflow-0.12.1-cp27-cp27mu-linux_ppc64le.whl  /
COPY tensorflow_model_server /

RUN pip install /tensorflow-0.12.1-cp27-cp27mu-linux_ppc64le.whl

WORKDIR /

CMD ["/bin/bash"]
