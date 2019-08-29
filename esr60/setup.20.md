Add meta layers required to build firefox.

```
$ bitbake-layers -F add-layer \$(pwd)/../meta-rust
$ bitbake-layers -F add-layer \$(pwd)/../meta-browser
```

Append the firefox configuration to auto.conf.

```
$ cat ~/firefox.conf >> conf/auto.conf
```
