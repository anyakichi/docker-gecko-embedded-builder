ARG builder_base="anyakichi/yocto-builder:xenial-rocko"
FROM ${builder_base}

COPY extract.15.md /etc/buildenv.d/
COPY extract.99.md /etc/buildenv.d/
COPY setup.15.md /etc/buildenv.d/

ARG yocto_machine
ARG meta_rzg2_version
ENV \
  YOCTO_MACHINE=${yocto_machine:-ek874} \
  YOCTO_BITBAKE_TARGET=core-image-weston \
  META_RZG2_VERSION=${meta_rzg2_version:-1.0.1-update1}
