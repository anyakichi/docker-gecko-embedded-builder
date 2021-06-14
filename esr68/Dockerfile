ARG builder_base="anyakichi/yocto-builder"
FROM ${builder_base}

RUN \
  apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    software-properties-common \
  && add-apt-repository -y ppa:ubuntu-toolchain-r/test \
  && apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    gcc-7 g++-7 \
  && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 10 --slave /usr/bin/g++ g++ /usr/bin/g++-5 \
  && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 20 --slave /usr/bin/g++ g++ /usr/bin/g++-7 \
  && rm -rf /var/lib/apt/lists/*

USER builder
COPY firefox.conf /home/builder/

USER root
COPY extract.20.md /etc/buildenv.d/
COPY setup.20.md /etc/buildenv.d/
