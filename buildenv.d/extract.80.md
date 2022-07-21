Clone the repositories required to build firefox ${FIREFOX_VERSION}.

```
$ git clone -b firefox-${FIREFOX_VERSION}-wip https://github.com/webdino/meta-browser.git

$ git clone https://github.com/meta-rust/meta-rust.git
$ git -C meta-rust pull https://github.com/mlilien/meta-rust/ 1.61.0

$ git clone https://github.com/webdino/meta-clang.git
$ if git -C meta-clang rev-parse --verify origin/${YOCTO_BRANCH} &>/dev/null; then \
    git -C meta-clang checkout ${YOCTO_BRANCH}; \
  fi
```
