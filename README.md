# linux-administrator-advanced-level
## Администратор Linux. Продвинутый уровень
### Занятие 1. Обновление ядра системы

#### Ядро до обновления
pavlikspb@test:~$ uname -r
7.0.0-34-generic

#### Ядро после обновления
pavlikspb@test:~$ uname -r
7.2.6-070206-generic

#### Ход работы
'''pavlikspb@test:~$ mkdir kernel && cd kernel
pavlikspb@test:~/kernel$ wget https://kernel.ubuntu.com/mainline/v7.2.6/amd64/linux-headers-7.2.6-070206-generic_7.2.6-070206.202609141300_amd64.deb
--2026-10-06 08:17:24--  https://kernel.ubuntu.com/mainline/v7.2.6/amd64/linux-headers-7.2.6-070206-generic_7.2.6-070206.202609141300_amd64.deb
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... 185.125.189.74, 185.125.189.75, 185.125.189.76
Connecting to kernel.ubuntu.com (kernel.ubuntu.com)|185.125.189.74|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4180574 (4.0M) [application/vnd.debian.binary-package]
Saving to: ‘linux-headers-7.2.6-070206-generic_7.2.6-070206.202609141300_amd64.deb’

linux-headers-7.2.6-070206-generic_7.2.6 100%[================================================================================>]   3.99M  7.87MB/s    in 0.5s

2026-10-06 08:17:26 (7.87 MB/s) - ‘linux-headers-7.2.6-070206-generic_7.2.6-070206.202609141300_amd64.deb’ saved [4180574/4180574]

pavlikspb@test:~/kernel$ wget https://kernel.ubuntu.com/mainline/v7.2.6/amd64/linux-headers-7.2.6-070206_7.2.6-070206.202609141300_all.deb
--2026-10-06 08:18:02--  https://kernel.ubuntu.com/mainline/v7.2.6/amd64/linux-headers-7.2.6-070206_7.2.6-070206.202609141300_all.deb
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... 185.125.189.74, 185.125.189.75, 185.125.189.76
Connecting to kernel.ubuntu.com (kernel.ubuntu.com)|185.125.189.74|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15026576 (14M) [application/vnd.debian.binary-package]
Saving to: ‘linux-headers-7.2.6-070206_7.2.6-070206.202609141300_all.deb’

linux-headers-7.2.6-070206_7.2.6-070206. 100%[================================================================================>]  14.33M  7.60MB/s    in 1.9s

2026-10-06 08:18:05 (7.60 MB/s) - ‘linux-headers-7.2.6-070206_7.2.6-070206.202609141300_all.deb’ saved [15026576/15026576]

pavlikspb@test:~/kernel$ wget https://kernel.ubuntu.com/mainline/v7.2.6/amd64/linux-image-unsigned-7.2.6-070206-generic_7.2.6-070206.202609141300_amd64.deb
--2026-10-06 08:18:25--  https://kernel.ubuntu.com/mainline/v7.2.6/amd64/linux-image-unsigned-7.2.6-070206-generic_7.2.6-070206.202609141300_amd64.deb
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... 185.125.189.74, 185.125.189.76, 185.125.189.75
Connecting to kernel.ubuntu.com (kernel.ubuntu.com)|185.125.189.74|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17653952 (17M) [application/vnd.debian.binary-package]
Saving to: ‘linux-image-unsigned-7.2.6-070206-generic_7.2.6-070206.202609141300_amd64.deb’

linux-image-unsigned-7.2.6-070206-generi 100%[================================================================================>]  16.84M  10.9MB/s    in 1.5s

2026-10-06 08:18:27 (10.9 MB/s) - ‘linux-image-unsigned-7.2.6-070206-generic_7.2.6-070206.202609141300_amd64.deb’ saved [17653952/17653952]

pavlikspb@test:~/kernel$ wget https://kernel.ubuntu.com/mainline/v7.2.6/amd64/linux-modules-7.2.6-070206-generic_7.2.6-070206.202609141300_amd64.deb
--2026-10-06 08:18:48--  https://kernel.ubuntu.com/mainline/v7.2.6/amd64/linux-modules-7.2.6-070206-generic_7.2.6-070206.202609141300_amd64.deb
Resolving kernel.ubuntu.com (kernel.ubuntu.com)... 185.125.189.75, 185.125.189.76, 185.125.189.74
Connecting to kernel.ubuntu.com (kernel.ubuntu.com)|185.125.189.75|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 171468992 (164M) [application/vnd.debian.binary-package]
Saving to: ‘linux-modules-7.2.6-070206-generic_7.2.6-070206.202609141300_amd64.deb’

linux-modules-7.2.6-070206-generic_7.2.6-070206.20260914130 100%[========================================================================================================================================>] 163.53M  12.1MB/s    in 14s

2026-10-06 08:19:03 (11.7 MB/s) - ‘linux-modules-7.2.6-070206-generic_7.2.6-070206.202609141300_amd64.deb’ saved [171468992/171468992]

pavlikspb@test:~/kernel$ sudo dpkg -i *.deb
Selecting previously unselected package linux-headers-7.2.6-070206-generic.
(Reading database ... 132380 files and directories currently installed.)
Preparing to unpack linux-headers-7.2.6-070206-generic_7.2.6-070206.202609141300_amd64.deb ...
Unpacking linux-headers-7.2.6-070206-generic (7.2.6-070206.202609141300) ...
Selecting previously unselected package linux-headers-7.2.6-070206.
Preparing to unpack linux-headers-7.2.6-070206_7.2.6-070206.202609141300_all.deb ...
Unpacking linux-headers-7.2.6-070206 (7.2.6-070206.202609141300) ...
Selecting previously unselected package linux-image-unsigned-7.2.6-070206-generic.
Preparing to unpack linux-image-unsigned-7.2.6-070206-generic_7.2.6-070206.202609141300_amd64.deb ...
Unpacking linux-image-unsigned-7.2.6-070206-generic (7.2.6-070206.202609141300) ...
Selecting previously unselected package linux-modules-7.2.6-070206-generic.
Preparing to unpack linux-modules-7.2.6-070206-generic_7.2.6-070206.202609141300_amd64.deb ...
Unpacking linux-modules-7.2.6-070206-generic (7.2.6-070206.202609141300) ...
Setting up linux-headers-7.2.6-070206 (7.2.6-070206.202609141300) ...
Setting up linux-modules-7.2.6-070206-generic (7.2.6-070206.202609141300) ...
Setting up linux-headers-7.2.6-070206-generic (7.2.6-070206.202609141300) ...
Setting up linux-image-unsigned-7.2.6-070206-generic (7.2.6-070206.202609141300) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-7.0.0-38-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-7.0.0-38-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-7.2.6-070206-generic
I: /boot/initrd.img is now a symlink to initrd.img-7.2.6-070206-generic
Processing triggers for linux-image-unsigned-7.2.6-070206-generic (7.2.6-070206.202609141300) ...
/etc/kernel/postinst.d/dracut:
dracut: Generating /boot/initrd.img-7.2.6-070206-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/50-cloudimg-settings.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-7.2.6-070206-generic
Found initrd image: /boot/initrd.img-7.2.6-070206-generic
Found linux image: /boot/vmlinuz-7.0.0-38-generic
Found initrd image: /boot/initrd.img-7.0.0-38-generic
Found linux image: /boot/vmlinuz-7.0.0-34-generic
Found initrd image: /boot/initrd.img-7.0.0-34-generic
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
pavlikspb@test:~/kernel$ ls -al /boot/
total 241316
drwxr-xr-x  5 root root     4096 Oct  6 08:23 .
drwxr-xr-x 19 root root     4096 Oct  3 10:20 ..
-rw-------  1 root root 11018537 Sep  2 09:35 System.map-7.0.0-34-generic
-rw-------  1 root root 11028836 Sep  4 07:31 System.map-7.0.0-38-generic
-rw-------  1 root root 11964070 Sep 14 13:00 System.map-7.2.6-070206-generic
-rw-r--r--  1 root root   308473 Sep  2 09:35 config-7.0.0-34-generic
-rw-r--r--  1 root root   308501 Sep  4 07:31 config-7.0.0-38-generic
-rw-r--r--  1 root root   307746 Sep 14 13:00 config-7.2.6-070206-generic
drwx------  3 root root      512 Jan  1  1970 efi
drwxr-xr-x  6 root root     4096 Oct  6 08:23 grub
lrwxrwxrwx  1 root root       31 Oct  6 08:23 initrd.img -> initrd.img-7.2.6-070206-generic
-rw-r--r--  1 root root 72091068 Sep 27 16:27 initrd.img-7.0.0-34-generic
-rw-------  1 root root 43855398 Oct  3 07:22 initrd.img-7.0.0-38-generic
-rw-------  1 root root 43922568 Oct  6 08:23 initrd.img-7.2.6-070206-generic
lrwxrwxrwx  1 root root       27 Oct  6 08:23 initrd.img.old -> initrd.img-7.0.0-38-generic
drwx------  2 root root    16384 Sep 27 16:28 lost+found
lrwxrwxrwx  1 root root       28 Oct  6 08:23 vmlinuz -> vmlinuz-7.2.6-070206-generic
-rw-------  1 root root 17303944 Sep  2 09:37 vmlinuz-7.0.0-34-generic
-rw-------  1 root root 17320328 Sep  4 07:54 vmlinuz-7.0.0-38-generic
-rw-------  1 root root 17621504 Sep 14 13:00 vmlinuz-7.2.6-070206-generic
lrwxrwxrwx  1 root root       24 Oct  6 08:23 vmlinuz.old -> vmlinuz-7.0.0-38-generic
pavlikspb@test:~/kernel$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/50-cloudimg-settings.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-7.2.6-070206-generic
Found initrd image: /boot/initrd.img-7.2.6-070206-generic
Found linux image: /boot/vmlinuz-7.0.0-38-generic
Found initrd image: /boot/initrd.img-7.0.0-38-generic
Found linux image: /boot/vmlinuz-7.0.0-34-generic
Found initrd image: /boot/initrd.img-7.0.0-34-generic
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
pavlikspb@test:~/kernel$ sudo grub-set-default 0
pavlikspb@test:~/kernel$ sudo reboot'''





