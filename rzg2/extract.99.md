Show a extra process that you must do manually because it requires some
proprietary packages and can't be automated.

```
$ printf "\
\n================================================================================\
\nDownload and extract the proprietary directory for RZ/G2, then execute this\
\ncommand.\
\n\
\n  $ (cd meta-rzg2 && sh docs/sample/copyscript/copy_proprietary_softwares.sh -f ../proprietary)\
\n\
\nAdditionaly, apply proprietary patches if necessary.\
\n\
\n  $ (cd meta-rzg2 && git am ../0001-BSP-${META_RZG2_VERSION}-add-support-HDMI.patch)\
\n================================================================================\n"
```
