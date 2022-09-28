Clone the repositories required to build firefox ${FIREFOX_VERSION}.

```
$ git clone -b firefox-${FIREFOX_VERSION}-wip https://github.com/webdino/meta-browser.git

$ git clone https://github.com/meta-rust/meta-rust.git
$ git -C meta-rust checkout 59c4377bdbc67aa306068d19b016136998fadcec

$ git clone https://github.com/webdino/meta-clang.git
$ if git -C meta-clang rev-parse --verify origin/${YOCTO_BRANCH} &>/dev/null; then \
    git -C meta-clang checkout ${YOCTO_BRANCH}; \
  fi
```
