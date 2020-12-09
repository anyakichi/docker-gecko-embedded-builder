ARG builder_base="anyakichi/yocto-builder"
FROM ${builder_base}

RUN \
  apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    software-properties-common \
  && add-apt-repository ppa:ubuntu-toolchain-r/test \
  && apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    gcc-7 g++-7 \
  && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 10 --slave /usr/bin/g++ g++ /usr/bin/g++-5 \
  && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 20 --slave /usr/bin/g++ g++ /usr/bin/g++-7

USER builder
COPY firefox.conf /home/builder/

RUN \
  git clone --branch esr68 --depth 1 https://github.com/mozilla/gecko-dev.git /home/builder/gecko-dev
RUN \
  export SHELL=/bin/sh && \
  (cd /home/builder/gecko-dev && ./mach bootstrap --application-choice browser --no-interactive) \
  && rm -rf /home/builder/gecko-dev

USER root

RUN \
  rm -rf /var/lib/apt/lists/*

COPY extract.20.md /etc/buildenv.d/
COPY setup.20.md /etc/buildenv.d/
