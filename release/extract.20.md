Clone the repositories required to build firefox ${FIREFOX_VERSION}.

```
$ git clone -b firefox-${FIREFOX_VERSION}-wip https://github.com/webdino/meta-browser.git

$ git clone https://github.com/meta-rust/meta-rust.git
$ git -C meta-rust checkout 0fffd992ee560bbfd682d3ef94b7636670e6fd56
$ git -C meta-rust revert 647b976da2a9161ceb01ad477216480fc1c88af8 < /dev/null

$ git clone -b rocko-again-9.0.0 https://github.com/webdino/meta-clang.git
```
