Clone the repositories required to build firefox ${FIREFOX_VERSION}.

```
$ git clone -b gem-firefox-91.13.0esr https://github.com/webdino/meta-browser.git

$ git clone https://github.com/meta-rust/meta-rust.git
$ if git -C meta-rust rev-parse --verify origin/${YOCTO_BRANCH} &>/dev/null; then \
    git -C meta-rust checkout ${YOCTO_BRANCH}; \
  fi
$ if [[ "\${YOCTO_BRANCH}" =~ ^rocko|dunfell$ ]]; then \
    git -C meta-rust checkout 1b59fd45906082c978d0a0a6e4e51a0ea4aa32c7; \
    git -C meta-rust revert 647b976da2a9161ceb01ad477216480fc1c88af8 < /dev/null; \
  fi

$ git clone https://github.com/webdino/meta-clang.git
$ if git -C meta-clang rev-parse --verify origin/${YOCTO_BRANCH} &>/dev/null; then \
    git -C meta-clang checkout ${YOCTO_BRANCH}; \
  fi
$ if [[ "\${YOCTO_BRANCH}" == rocko ]]; then \
    git -C meta-clang checkout rocko-again-9.0.0; \
  fi
```

Update the pixman package if it is old.

```
$ if [[ -e poky/meta/recipes-graphics/xorg-lib/pixman_0.34.0.bb ]]; then \
    git -C poky cherry-pick bdb23bd1e3a17594f0352fabf3df90011940b0a0; \
  fi
```
