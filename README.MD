# Applied Yocto Project using Raspberry Pi 5

This repository includes documentation and a course learning from the Udemy course [Applied Yocto Project using Raspberry Pi 5 (Embedded Linux)](https://www.udemy.com/course/yocto-project/).

> I'm actually applying the learning on a Raspberry Pi 4 board.

#### References

- [Yocto Documentation](https://docs.yoctoproject.org/)
- [OpenEmbedded Layers](https://layers.openembedded.org/layerindex/branch/master/layers/
)

## Steps

Build Host Packages: 
```shell
sudo apt install build-essential chrpath cpio debianutils diffstat file gawk gcc git iputils-ping libacl1 liblz4-tool locales python3 python3-git python3-jinja2 python3-pexpect python3-pip python3-subunit socat texinfo unzip wget xz-utils zstd
```

Download Poky and checkout to latest stable version:
```shell
git clone https://git.yoctoproject.org/poky/
cd poky
git checkout scarhgap
```

Download [meta-oe](https://git.openembedded.org/meta-openembedded/) layer:

```shell
git clone https://git.openembedded.org/meta-openembedded/ -b scarthgap
```
And updated the `poky/build/conf/bblayers.conf` with the new layer.


Download [meta-q5](https://github.com/meta-qt5/meta-qt5.git) layer:
```shell
git clone https://github.com/meta-qt5/meta-qt5.git -b scarthgap
```
And updated the `poky/build/conf/bblayers.conf` with the new layer.

Download [meta-raspberrypi](git://git.yoctoproject.org/meta-raspberrypi) layer:
```shell
git clone git://git.yoctoproject.org/meta-raspberrypi -b scarthgap
```
and update the `poky/build/conf/bblayers.conf` with the new layer.

Added the `MACHINE` variable on `poky/build/conf/local.conf`:
```python
# Lucasgb7 modifications
MACHINE = "raspberrypi4-64"
```

The `bblayers.conf` file should look like this:
```python
# POKY_BBLAYERS_CONF_VERSION is increased each time build/conf/bblayers.conf
# changes incompatibly
POKY_BBLAYERS_CONF_VERSION = "2"

BBPATH = "${TOPDIR}"
BBFILES ?= ""

BBLAYERS ?= " \
  ${TOPDIR}/../meta \
  ${TOPDIR}/../meta-poky \
  ${TOPDIR}/../meta-yocto-bsp \
  ${TOPDIR}/../meta-openembedded \
  ${TOPDIR}/../meta-qt5 \
  ${TOPDIR}/../meta-raspberrypi \
  "
```