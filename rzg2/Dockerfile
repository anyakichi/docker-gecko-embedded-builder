FROM anyakichi/yocto-builder:xenial-rocko

COPY extract.15.md /etc/buildenv.d/
COPY setup.15.md /etc/buildenv.d/
COPY extract.txt /tmp

ENV \
  YOCTO_MACHINE=ek874 \
  YOCTO_BITBAKE_TARGET=core-image-weston
