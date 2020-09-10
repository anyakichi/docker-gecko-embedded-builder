ARG builder_base="anyakichi/yocto-builder"
FROM ${builder_base}

RUN \
  apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    autoconf2.13 \
    build-essential \
    libasound2-dev \
    libcurl4-openssl-dev \
    libdbus-1-dev \
    libdbus-glib-1-dev \
    libgconf2-dev \
    libgtk-3-dev \
    libgtk2.0-dev \
    libpulse-dev \
    libx11-xcb-dev \
    libxt-dev \
    nasm \
    nodejs \
    openjdk-8-jdk-headless \
    python-dbus \
    python-dev \
    python-pip \
    python-setuptools \
    software-properties-common \
    unzip \
    uuid \
    wget \
    xvfb \
    yasm \
    zip \
  && add-apt-repository ppa:ubuntu-toolchain-r/test \
  && apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    gcc-7 g++-7 \
  && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 10 --slave /usr/bin/g++ g++ /usr/bin/g++-5 \
  && update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-7 20 --slave /usr/bin/g++ g++ /usr/bin/g++-7 \
  && rm -rf /var/lib/apt/lists/*

USER builder
COPY firefox.conf /home/builder/

RUN \
  git clone --branch esr78 --depth 1 https://github.com/mozilla/gecko-dev.git /home/builder/gecko-dev
RUN \
  export SHELL=/bin/sh && \
  (cd /home/builder/gecko-dev && /bin/echo -e "2\n3\nY\nn\nn" | ./mach bootstrap) \
  && rm -rf /home/builder/gecko-dev

USER root

COPY extract.20.md /etc/buildenv.d/
COPY setup.20.md /etc/buildenv.d/
