Add meta layers required to build firefox.

```
$ bitbake-layers -F add-layer \$(pwd)/../meta-rust
$ bitbake-layers -F add-layer \$(pwd)/../meta-clang
$ bitbake-layers -F add-layer \$(pwd)/../meta-browser
```

Append the firefox configuration to auto.conf.

```
$ cat ~/firefox.conf >> conf/auto.conf
```

If BSP version is older than 1.0.5, mask openssl_debian.

```
$ [[ ${META_RZG2_BRANCH} < BSP-1.0.5 ]] && echo 'BBMASK .= "|openssl_debian"' >> conf/auto.conf
```
