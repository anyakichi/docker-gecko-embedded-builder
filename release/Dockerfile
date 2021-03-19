ARG builder_base="anyakichi/yocto-builder"
FROM ${builder_base}

RUN \
  apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    libcurl4-openssl-dev \
    mercurial \
    software-properties-common \
  && add-apt-repository -y ppa:ubuntu-toolchain-r/test \
  && apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    gcc-7 g++-7 \
  && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 10 --slave /usr/bin/g++ g++ /usr/bin/g++-5 \
  && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 20 --slave /usr/bin/g++ g++ /usr/bin/g++-7 \
  && rm /etc/apt/sources.list.d/ubuntu-toolchain-r-ubuntu-test-xenial.list* \
  && add-apt-repository -y ppa:deadsnakes/ppa \
  && apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    python3.8 python3.8-dev python3.8-distutils \
  && update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.5 10 --slave /usr/bin/python3-config python3-config /usr/bin/python3.5-config \
  && update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.8 20 --slave /usr/bin/python3-config python3-config /usr/bin/python3.8-config \
  && rm /etc/apt/sources.list.d/deadsnakes-ubuntu-ppa-xenial.list*

USER builder
COPY firefox.conf /home/builder/

RUN \
  wget -O /home/builder/bootstrap.py https://hg.mozilla.org/mozilla-central/raw-file/default/python/mozboot/bin/bootstrap.py
RUN \
  export SHELL=/bin/sh && \
  (cd /home/builder && python3 bootstrap.py --application-choice=browser --no-interactive --vcs=git) \
  && rm -rf /home/builder/bootstrap.py /home/builder/mozilla-unified

USER root

RUN \
  rm -rf /var/lib/apt/lists/*

COPY extract.20.md /etc/buildenv.d/
COPY setup.20.md /etc/buildenv.d/

ENV FIREFOX_VERSION=86
