Checkout the specific revision of poky.

```
$ git -C poky checkout 7e7ee662f5dea4d090293045f7498093322802cc
```

Clone the repositories required to build the RZ/G2 series firmware.

```
$ git clone https://git.linaro.org/openembedded/meta-linaro.git
$ git -C meta-linaro checkout 75dfb67bbb14a70cd47afda9726e2e1c76731885

$ git clone https://git.openembedded.org/meta-openembedded
$ git -C meta-openembedded checkout 352531015014d1957d6444d114f4451e241c4d23

$ git clone http://git.yoctoproject.org/cgit.cgi/meta-gplv2
$ git -C meta-gplv2 checkout f875c60ecd6f30793b80a431a2423c4b98e51548

$ git clone https://github.com/meta-qt5/meta-qt5.git
$ git -C meta-qt5 checkout c1b0c9f546289b1592d7a895640de103723a0305

$ git clone -b BSP-1.0.0 https://github.com/renesas-rz/meta-rzg2.git
$ git -C meta-rzg2 cherry-pick 79dbcd79ed4e1192c408a60a17c70b14c6d0715e
```

Show a extra process that you must do manually because it requires some
proprietary packages and can't be automated.

```
$ cat /tmp/extract.txt
```
