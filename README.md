

# 首頁

> Ubuntu / ISO Builder / 探索筆記

| Link | GitHub |
| ---- | ------ |
| [ISO Builder 探索筆記](https://samwhelp.github.io/note-about-iso-builder/) | [GitHub](https://github.com/samwhelp/note-about-iso-builder) |
| [Ubuntu / ISO Builder / 探索筆記](https://samwhelp.github.io/note-about-ubuntu-iso-builder/) | [GitHub](https://github.com/samwhelp/note-about-ubuntu-iso-builder) |
| [Debian / ISO Builder / 探索筆記](https://samwhelp.github.io/note-about-debian-iso-builder/) | [GitHub](https://github.com/samwhelp/note-about-debian-iso-builder) |
| [ubuntu-iso-builder-maintain](https://samwhelp.github.io/ubuntu-iso-builder-maintain/) | [GitHub](https://github.com/samwhelp/ubuntu-iso-builder-maintain) |
| [Pacstall 探索筆記](https://samwhelp.github.io/note-about-pacstall/) | [GitHub](https://github.com/samwhelp/note-about-pacstall) |




## 主題

* [實作案例](#實作案例)
* [Docker](#docker)
* [Respin](#respin)
* [Boot ISO By GRUB](#boot-iso-by-grub)
* [Live Account](#live-account)
* [相關筆記](#相關筆記)




## 實作案例

| Link | GitHub |
| ---- | ------ |
| [ubuntu-iso-builder-template](https://samwhelp.github.io/ubuntu-iso-builder-template/) | [GitHub](https://github.com/samwhelp/ubuntu-iso-builder-template) |
| [ubuntu-iso-builder-engine-develop](https://samwhelp.github.io/ubuntu-iso-builder-engine-develop/) | [GitHub](https://github.com/samwhelp/ubuntu-iso-builder-engine-develop) |




## Docker

| Docker Image |
| ------------ |
| [distro-iso-builder-docker-image](https://github.com/samwhelp/distro-iso-builder-docker-image) |
| [ubuntu-docker-image](https://github.com/samwhelp/ubuntu-docker-image) |




## Respin

> [更多...](https://samwhelp.github.io/note-about-ubuntu-iso-builder/read/respin.html)

| Remix | Respin |
| ----- | ------ |
| [ubuntu-iso-builder-remix-gnome-shell](https://github.com/samwhelp/ubuntu-iso-builder-remix-gnome-shell) | [ubuntu-iso-builder-respin-gnome-shell](https://github.com/samwhelp/ubuntu-iso-builder-respin-gnome-shell) |
| [ubuntu-iso-builder-remix-kde-plasma](https://github.com/samwhelp/ubuntu-iso-builder-remix-kde-plasma) | [ubuntu-iso-builder-respin-kde-plasma](https://github.com/samwhelp/ubuntu-iso-builder-respin-kde-plasma) |
| [ubuntu-iso-builder-remix-xfce](https://github.com/samwhelp/ubuntu-iso-builder-remix-xfce) | [ubuntu-iso-builder-respin-xfce](https://github.com/samwhelp/ubuntu-iso-builder-respin-xfce) |
| [ubuntu-iso-builder-remix-lxqt](https://github.com/samwhelp/ubuntu-iso-builder-remix-lxqt) | [ubuntu-iso-builder-respin-lxqt](https://github.com/samwhelp/ubuntu-iso-builder-respin-lxqt) |
| [ubuntu-iso-builder-remix-mate](https://github.com/samwhelp/ubuntu-iso-builder-remix-mate) | [ubuntu-iso-builder-respin-mate](https://github.com/samwhelp/ubuntu-iso-builder-respin-mate) |
| [ubuntu-iso-builder-remix-cinnamon](https://github.com/samwhelp/ubuntu-iso-builder-remix-cinnamon) | [ubuntu-iso-builder-respin-cinnamon](https://github.com/samwhelp/ubuntu-iso-builder-respin-cinnamon) |
| [ubuntu-iso-builder-remix-budgie](https://github.com/samwhelp/ubuntu-iso-builder-remix-budgie) | [ubuntu-iso-builder-respin-budgie](https://github.com/samwhelp/ubuntu-iso-builder-respin-budgie) |


| Remix | Respin |
| ----- | ------ |
| [ubuntu-iso-builder-remix-lxqt-with-kwin](https://github.com/samwhelp/ubuntu-iso-builder-remix-lxqt-with-kwin) | [ubuntu-iso-builder-respin-lxqt-with-kwin](https://github.com/samwhelp/ubuntu-iso-builder-respin-lxqt-with-kwin) |
| [ubuntu-iso-builder-remix-mate-with-compiz](https://github.com/samwhelp/ubuntu-iso-builder-remix-mate-with-compiz) | [ubuntu-iso-builder-respin-mate-with-compiz](https://github.com/samwhelp/ubuntu-iso-builder-respin-mate-with-compiz) |




## Boot ISO By GRUB

> 將產出的「iso檔案」放置到「`/opt/iso/ubuntu/latest/ubuntu.iso`」這個路徑

> 產生一個檔案「`/boot/grub/custom.cfg`」，內容如下

``` sh
menuentry "Ubuntu Live ISO" --class Ubuntu {
	set iso_file="/opt/iso/ubuntu/latest/ubuntu.iso"
	search --set=iso_partition --no-floppy --file $iso_file
	probe --set=iso_partition_uuid --fs-uuid $iso_partition
	set img_dev="/dev/disk/by-uuid/$iso_partition_uuid"
	loopback loop ($iso_partition)$iso_file

	set extra_option=""
	#set extra_option="components quiet splash"

	set locale_option=""
	#set locale_option="locales=en_US.UTF-8"
	#set locale_option="locales=zh_TW.UTF-8"
	#set locale_option="locales=zh_CN.UTF-8"
	#set locale_option="locales=zh_HK.UTF-8"
	#set locale_option="locales=ja_JP.UTF-8"
	#set locale_option="locales=ko_KR.UTF-8"

	set boot_option="${locale_option} ${extra_option}"
	linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=${iso_file} ${boot_option}
	initrd (loop)/casper/initrd
}
```

> 重新開機後，就會在「GRUB」的開機選單，看到「`Ubuntu Live ISO`」這個選項。


> [/usr/share/initramfs-tools/scripts/casper](https://git.launchpad.net/ubuntu/+source/casper/tree/scripts/casper#n32)




## Live Account

| Account  | Value  |
| -------- | ------ |
| Username | `live` |
| Password |        |

> 目前沒有設定密碼


若想要更改目前帳號的密碼，可以執行下面指令

``` sh
sudo passwd $(whoami)
```


若想要移除目前帳號的密碼，可以執行下面指令

``` sh
sudo passwd -d $(whoami)
```




## 相關筆記

| Link | GitHub |
| ---- | ------ |
| [Ubuntu 探索筆記](https://samwhelp.github.io/note-about-ubuntu/) | [GitHub](https://github.com/samwhelp/note-about-ubuntu) |
| [Debian 探索筆記](https://samwhelp.github.io/note-about-debian/) | [GitHub](https://github.com/samwhelp/note-about-debian) |
| [Debian / ISO Builder / 探索筆記](https://samwhelp.github.io/note-about-debian-iso-builder/) | [GitHub](https://github.com/samwhelp/note-about-debian-iso-builder) |
| [Pacstall 探索筆記](https://samwhelp.github.io/note-about-pacstall/) | [GitHub](https://github.com/samwhelp/note-about-pacstall) |




## Samwhelp

* [個人筆記](https://samwhelp.github.io/book/)
