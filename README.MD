# Udemy Course: Applied Yocto Project using Raspberry Pi 5
Link: https://www.udemy.com/course/yocto-project/
Yocto Reference: https://docs.yoctoproject.org/

## Steps

Build Host Packages: 
```
$ sudo apt install build-essential chrpath cpio debianutils diffstat file gawk gcc git iputils-ping libacl1 liblz4-tool locales python3 python3-git python3-jinja2 python3-pexpect python3-pip python3-subunit socat texinfo unzip wget xz-utils zstd
```

Download Poky and checkout to latest stable version:
```
git clone https://git.yoctoproject.org/poky/
cd poky
git checkout scarhgap
```
