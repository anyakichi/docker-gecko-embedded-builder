Clone the repositories required to build firefox ${FIREFOX_VERSION}.

```
$ git clone -b firefox-${FIREFOX_VERSION}-wip https://github.com/webdino/meta-browser.git

$ git clone https://github.com/meta-rust/meta-rust.git
$ git -C meta-rust checkout 1b59fd45906082c978d0a0a6e4e51a0ea4aa32c7
$ git -C meta-rust revert 647b976da2a9161ceb01ad477216480fc1c88af8 < /dev/null

$ git clone -b rocko-again-9.0.0 https://github.com/webdino/meta-clang.git
```
