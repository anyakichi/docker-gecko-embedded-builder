Clone the repositories required to build firefox 60.

```
$ git clone -b firefox-60esr https://github.com/webdino/meta-browser.git

$ git clone https://github.com/webdino/meta-rust.git
$ git -C meta-rust checkout 4110f1d92af4dbcb73ed5ad6f18b25bd097451ae

$ git clone -b rocko-again https://github.com/webdino/meta-clang.git
```
