Clone the repositories required to build firefox ${FIREFOX_VERSION}.

```
$ git clone -b firefox-${FIREFOX_VERSION}-wip https://github.com/webdino/meta-browser.git

$ if [ ! -d meta-rust ]; then \
    git clone https://github.com/meta-rust/meta-rust.git; \
  fi
$ git -C meta-rust checkout 796da2dfb669f222d7fb82a9e1ffaf605d5ac16d

$ if [ ! -d meta-clang ]; then \
    git clone https://github.com/kraj/meta-clang.git; \
  fi
$ if git -C meta-clang rev-parse --verify origin/${YOCTO_BRANCH} &>/dev/null; then \
    git -C meta-clang checkout ${YOCTO_BRANCH}; \
  fi

$ if [ ! -d meta-openembedded ]; then \
    git clone https://git.openembedded.org/meta-openembedded; \
  fi
$ if git -C meta-openembedded rev-parse --verify origin/${YOCTO_BRANCH} &>/dev/null; then \
    git -C meta-openembedded checkout ${YOCTO_BRANCH}; \
  fi
```
