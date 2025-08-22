

## Link

* https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1431841
* https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1431841/comments/1
* https://packages.ubuntu.com/plucky/casper
* https://packages.ubuntu.com/plucky/amd64/casper/filelist




## losetup

``` sh
dpkg -S losetup
```

```
klibc-utils: /usr/lib/klibc/bin/losetup
mount: /usr/share/bash-completion/completions/losetup
mount: /usr/share/man/man8/losetup.8.gz
mount: /usr/sbin/losetup
```

> Google Search: [losetup casper mount](https://www.google.com/search?q=losetup+casper+mount)



## kernel package installed

``` sh
dpkg -l 'linux*'
```


## linux-image-generic

run

``` sh
apt-cache search linux-image-generic
```

show

```
linux-image-extra-virtual - Extra drivers for Virtual Linux kernel image
linux-image-extra-virtual-hwe-24.04 - Extra drivers for Virtual Linux kernel image
linux-image-extra-virtual-hwe-24.04-edge - Extra drivers for Virtual Linux kernel image
linux-image-generic - Generic Linux kernel image
linux-image-generic-hwe-24.04 - Generic Linux kernel image
linux-image-generic-hwe-24.04-edge - Generic Linux kernel image
linux-image-extra-virtual-6.14 - Extra drivers for Virtual Linux kernel image
linux-image-generic-6.14 - Generic Linux kernel image
```

run

``` sh
apt-cache show linux-image-generic | grep '^Depends'
```

show

```
Depends: linux-image-6.14.0-28-generic, linux-modules-extra-6.14.0-28-generic, linux-firmware, intel-microcode, amd64-microcode
Depends: linux-image-6.14.0-15-generic, linux-modules-extra-6.14.0-15-generic, linux-firmware, intel-microcode, amd64-microcode
```



chroot remove

``` sh
apt-get purge linux-image-6.14.0-28-generic linux-modules-extra-6.14.0-28-generic
```

chroot install

``` sh
apt-get install linux-image-6.14.0-27-generic linux-modules-extra-6.14.0-27-generic linux-firmware intel-microcode amd64-microcode
```




## linux-image-generic-hwe-24.04

run

``` sh
apt-cache show linux-image-generic-hwe-24.04 | grep '^Depends'
```

show

```
Depends: linux-image-6.14.0-28-generic, linux-modules-extra-6.14.0-28-generic, linux-firmware, intel-microcode, amd64-microcode
Depends: linux-image-6.14.0-15-generic, linux-modules-extra-6.14.0-15-generic, linux-firmware, intel-microcode, amd64-microcode
```
