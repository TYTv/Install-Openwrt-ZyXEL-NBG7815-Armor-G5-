# Install-Openwrt-ZyXEL-NBG7815-Armor-G5-

=== uboot ===
(U-Boot 2016.01 (Jan 06 2020 - 08:24:12 +0000)    <--- can only be found uboot now, but not found zloader)


IPQ807x# printenv serverip
serverip=192.168.1.99               ---> setting PC ip address 192.168.1.99 and run tftpd64 program

IPQ807x# tftpboot openwrt-ipq807x-generic-zyxel_nbg7815-initramfs-uImage.itb
ipq807x_eth_halt: done
eth0 PHY0 Down Speed :10 Half duplex
eth0 PHY1 Down Speed :10 Half duplex
eth0 PHY2 Down Speed :10 Half duplex
eth0 PHY3 up Speed :1000 Full duplex
eth0 PHY4 Down Speed :10 Half duplex
10M speed not supported
ipq807x_eth_init: done
Using eth0 device
TFTP from server 192.168.1.99; our IP address is 192.168.1.1
Filename 'openwrt-ipq807x-generic-zyxel_nbg7815-initramfs-uImage.itb'.
Load address: 0x44000000
Loading: *
Got TFTP_OACK: TFTP remote port: changes from 69 to 58367
#################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #####
         1.9 MiB/s
done
Bytes transferred = 12473096 (be5308 hex)
ipq807x_eth_halt: done

IPQ807x# bootm               ---> openwrt run in ram


=== ethernet connect to internet ===
root@OpenWrt:/# ping www.hinet.net
PING www.hinet.net (2001:b000:580::7): 56 data bytes
64 bytes from 2001:b000:580::7: seq=0 ttl=57 time=14.781 ms
64 bytes from 2001:b000:580::7: seq=1 ttl=57 time=17.927 ms
64 bytes from 2001:b000:580::7: seq=2 ttl=57 time=14.658 ms
64 bytes from 2001:b000:580::7: seq=3 ttl=57 time=26.638 ms
64 bytes from 2001:b000:580::7: seq=4 ttl=57 time=26.498 ms
^C
--- www.hinet.net ping statistics ---
5 packets transmitted, 5 packets received, 0% packet loss
round-trip min/avg/max = 14.658/20.100/26.638 ms
root@OpenWrt:/#

=== on line install kmod-mtd-rw ===
opkg update
opkg install kmod-mtd-rw
insmod /lib/modules/6.1.33/mtd-rw.ko i_want_a_brick=1
mtd unlock /dev/mtd0
mtd unlock /dev/mtd1
mtd unlock /dev/mtd2
mtd unlock /dev/mtd3
mtd unlock /dev/mtd4
mtd unlock /dev/mtd5
mtd unlock /dev/mtd6
mtd unlock /dev/mtd7
mtd unlock /dev/mtd8
mtd unlock /dev/mtd9
mtd unlock /dev/mtd10
mtd unlock /dev/mtd11
mtd unlock /dev/mtd12
mtd unlock /dev/mtd13
mtd unlock /dev/mtd14
mtd unlock /dev/mtd15
mtd unlock /dev/mtd16
mtd unlock /dev/mtd17
mtd unlock /dev/mtd18
mtd unlock /dev/mtd19
mtd unlock /dev/mtd20
mtd unlock /dev/mtd21

=== recovery to factory mtd ===
(via winscp copy backup files(OpenWrt.mtd0~21.bin) to system)

mtd write OpenWrt.mtd0.bin /dev/mtd0
mtd write OpenWrt.mtd1.bin /dev/mtd1
mtd write OpenWrt.mtd2.bin /dev/mtd2
mtd write OpenWrt.mtd3.bin /dev/mtd3
mtd write OpenWrt.mtd4.bin /dev/mtd4
mtd write OpenWrt.mtd5.bin /dev/mtd5
mtd write OpenWrt.mtd6.bin /dev/mtd6
mtd write OpenWrt.mtd7.bin /dev/mtd7
mtd write OpenWrt.mtd8.bin /dev/mtd8
mtd write OpenWrt.mtd9.bin /dev/mtd9
mtd write OpenWrt.mtd10.bin /dev/mtd10
mtd write OpenWrt.mtd11.bin /dev/mtd11
mtd write OpenWrt.mtd12.bin /dev/mtd12
mtd write OpenWrt.mtd13.bin /dev/mtd13
mtd write OpenWrt.mtd14.bin /dev/mtd14
mtd write OpenWrt.mtd15.bin /dev/mtd15
mtd write OpenWrt.mtd16.bin /dev/mtd16
mtd write OpenWrt.mtd17.bin /dev/mtd17
mtd write OpenWrt.mtd18.bin /dev/mtd18
mtd write OpenWrt.mtd19.bin /dev/mtd19
mtd write OpenWrt.mtd20.bin /dev/mtd20
mtd write OpenWrt.mtd21.bin /dev/mtd21

reboot

(Zyxel zloader v1.0.0 (2020-01-06 - 08:24)   <--- can now be found)

=== zLoader unlock ===
(boot to zloader and press any key enter command line)
NBG7815>
NBG7815> ATSE NBG7815
530591784140
NBG7815>

(via winscp copy tool.sh to linux system)
felix@ubuntu:~$ chmod -R 777 tool.sh
felix@ubuntu:~$ ./tool.sh 530591784140
ATEN 1,1110AF65
felix@ubuntu:~$

NBG7815>
NBG7815> ATEN 1,1110AF65
NBG7815> ATGU
ZYXEL#




=== openwrt uImage.itb load to ram ===
ZYXEL# tftpboot openwrt-ipq807x-generic-zyxel_nbg7815-initramfs-uImage.itb
ipq807x_eth_halt: done
eth0 PHY0 Down Speed :10 Half duplex
eth0 PHY1 Down Speed :10 Half duplex
eth0 PHY2 Down Speed :10 Half duplex
eth0 PHY3 Down Speed :10 Half duplex
eth0 PHY4 up Speed :1000 Full duplex
eth0 PHY5 Down Speed :10000 Full duplex
ipq807x_eth_init: done
Using eth0 device
TFTP from server 192.168.1.99; our IP address is 192.168.1.1
Filename 'openwrt-ipq807x-generic-zyxel_nbg7815-initramfs-uImage.itb'.
Load address: 0x44000000
Loading: ipq807x_eth_halt: done

Abort
ZYXEL# <INTERRUPT>
ZYXEL# tftpboot openwrt-qualcommax-ipq807x-zyxel_nbg7815-initramfs-uImage.itb
ipq807x_eth_halt: done
eth0 PHY0 Down Speed :10 Half duplex
eth0 PHY1 Down Speed :10 Half duplex
eth0 PHY2 Down Speed :10 Half duplex
eth0 PHY3 up Speed :1000 Full duplex
eth0 PHY4 up Speed :1000 Full duplex
eth0 PHY5 Down Speed :10000 Full duplex
ipq807x_eth_init: done
Using eth0 device
TFTP from server 192.168.1.99; our IP address is 192.168.1.1
Filename 'openwrt-qualcommax-ipq807x-zyxel_nbg7815-initramfs-uImage.itb'.
Load address: 0x44000000
Loading: *
Got TFTP_OACK: TFTP remote port: changes from 69 to 63650
#################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         ##########################
         1.9 MiB/s
done
Bytes transferred = 12773620 (c2e8f4 hex)
ipq807x_eth_halt: done
ZYXEL# bootm



=== fdisk ===



=== flash openwrt sysupgrade.bin ===
(via winscp copy .bin to system)

root@OpenWrt:~# sysupgrade -n /tmp/openwrt-.zyxel-nbg7815-nss-6.1.-20230929-qualcommax-ipq807x-zyxel_nbg7815-squashfs-sysupgrade.bin
Sat Oct 21 06:16:28 UTC 2023 upgrade: Commencing upgrade. Closing all shell sessions.
Sat Oct 21 06:16:28 UTC 2023 upgrade: Sending TERM to remaining processes ...
Sat Oct 21 06:16:28 UTC 2023 upgrade: Sending signal TERM to sleep (3735)
Sat Oct 21 06:16:32 UTC 2023 upgrade: Sending KILL to remaining processes ...
[ 1253.147912] stage2 (3744): drop_caches: 3
Sat Oct 21 06:16:38 UTC 2023 upgrade: Switching to ramdisk...
[ 1254.472546] EXT4-fs (loop0): unmounting filesystem.
Sat Oct 21 06:16:40 UTC 2023 upgrade: Performing system upgrade...
cut: standard output: Broken pipe
flashing kernel to /dev/mmcblk0p3
flashing rootfs to /dev/mmcblk0p4
[ 1256.596535] loop0: detected capacity change from 0 to 51200
Format new rootfs_data at position 36700160.
mke2fs 1.47.0 (5-Feb-2023)
Creating filesystem with 25600 1k blocks and 6400 inodes
Filesystem UUID: cf3c3f01-4e92-43ed-b575-201ea0b1799d
Superblock backups stored on blocks:
        8193, 24577

Allocating group tables: done
Writing inode tables: done
Creating journal (1024 blocks): done
Writing superblocks and filesystem accounting information: done

[ 1256.711125] EXT4-fs (loop0): mounted filesystem with ordered data mode. Quota mode: disabled.
Saving config to rootfs_data at position 36700160.
cp: can't st[ 1256.718802] EXT4-fs (loop0): unmounting filesystem.
at '': No such file or directory
umount: can't unmount /dev: Resource busy
umount: can't unmount /tmp: Resource busy
[ 1257.183067] remoteproc remoteproc0: stopped remote processor cd00000.q6v5_wcss
[ 1257.693897] qcom_scm firmware:scm: No available mechanism for setting download mode
[ 1257.693979] reboot: Restarting system





