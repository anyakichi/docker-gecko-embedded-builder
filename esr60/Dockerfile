ARG builder_base=rgz2
FROM anyakichi/gecko-embedded-builder:${builder_base}

RUN \
  apt-get update \
  && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    autoconf2.13 \
    clang \
    clang-3.9 \
    llvm \
    llvm-3.9 \
  && rm -rf /var/lib/apt/lists/*

USER builder
COPY firefox.conf /home/builder/

USER root

COPY extract.20.md /etc/buildenv.d/
COPY setup.20.md /etc/buildenv.d/
