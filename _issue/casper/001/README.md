

## Search

* [mount: /cdrom/casper/filesystem.squashfs](https://www.google.com/search?q=mount:+/cdrom/casper/filesystem.squashfs)




## Link

* https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1431841
* https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1431841/comments/1
* https://packages.ubuntu.com/plucky/casper
* https://packages.ubuntu.com/plucky/amd64/casper/filelist




## article

* [install linux mint](https://amitmason.blogspot.com/2018/07/linux-mint.html)




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

run

``` sh
dpkg -l 'linux*'
```

show

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                   Version                         Architecture Description
+++-======================================-===============================-============-=============================================
ii  linux-base                             4.10.1ubuntu2                   all          Linux image base package
ii  linux-firmware                         20250317.git1d4c88ee-0ubuntu1.5 amd64        Firmware for Linux kernel drivers
un  linux-firmware-raspi2                  <none>                          <none>       (no description available)
un  linux-firmware-snapdragon              <none>                          <none>       (no description available)
un  linux-headers                          <none>                          <none>       (no description available)
un  linux-headers-6.14.0-28-generic        <none>                          <none>       (no description available)
un  linux-headers-686-pae                  <none>                          <none>       (no description available)
un  linux-headers-amd64                    <none>                          <none>       (no description available)
un  linux-headers-generic                  <none>                          <none>       (no description available)
un  linux-image                            <none>                          <none>       (no description available)
ii  linux-image-6.14.0-28-generic          6.14.0-28.28                    amd64        Signed kernel image generic
un  linux-image-unsigned-6.14.0-28-generic <none>                          <none>       (no description available)
un  linux-initramfs-tool                   <none>                          <none>       (no description available)
un  linux-kernel-headers                   <none>                          <none>       (no description available)
ii  linux-libc-dev:amd64                   6.14.0-28.28                    amd64        Linux Kernel Headers for development
rc  linux-modules-6.14.0-27-generic        6.14.0-27.27                    amd64        Linux kernel extra modules for version 6.14.0
ii  linux-modules-6.14.0-28-generic        6.14.0-28.28                    amd64        Linux kernel extra modules for version 6.14.0
ii  linux-modules-extra-6.14.0-28-generic  6.14.0-28.28                    amd64        Linux kernel extra modules for version 6.14.0
un  linux-perf                             <none>                          <none>       (no description available)
un  linux-restricted-common                <none>                          <none>       (no description available)
ii  linux-sysctl-defaults                  4.10.1ubuntu2                   all          default sysctl configuration for Linux
un  linux-tools                            <none>                          <none>       (no description available)
```


run

``` sh
ls /boot/ -al
```

show


```
total 97412
drwxr-xr-x  3 root root     4096 Aug 23 06:53 .
drwxr-xr-x 17 root root     4096 Aug 22 17:47 ..
-rw-r--r--  1 root root   296778 Jul 23 18:01 config-6.14.0-28-generic
drwxr-xr-x  2 root root     4096 Aug 22 18:01 grub
lrwxrwxrwx  1 root root       28 Aug 23 06:46 initrd.img -> initrd.img-6.14.0-28-generic
-rw-r--r--  1 root root 73375610 Aug 23 06:46 initrd.img-6.14.0-28-generic
lrwxrwxrwx  1 root root       28 Aug 23 06:51 initrd.img.old -> initrd.img-6.14.0-28-generic
-rw-------  1 root root 10287886 Jul 23 18:01 System.map-6.14.0-28-generic
lrwxrwxrwx  1 root root       25 Aug 23 06:46 vmlinuz -> vmlinuz-6.14.0-28-generic
-rw-------  1 root root 15772040 Jul 23 18:08 vmlinuz-6.14.0-28-generic
lrwxrwxrwx  1 root root       25 Aug 23 06:51 vmlinuz.old -> vmlinuz-6.14.0-28-generic
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
