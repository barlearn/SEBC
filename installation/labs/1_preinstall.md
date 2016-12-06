Swappiness
file located in /proc/sys/vm and is named “swappiness”.
Temporary change lost on reboot
sudo sysctl vm.swappiness=1

permanent changes to /etc/sysctl.conf
by add the below line
vm.swappiness=”1”

Mount attributes of all volumes
Fdisk - l
Sfdisk –l -uM
Cfdisk /dev/xvde
df -h
lsblk
blkid

Reserve space of any non-root, ext-based volumes
tune2fs -l /dev/xvde
root@\Barlearn1$ tune2fs -l /dev/xvde
tune2fs 1.41.12 (17-May-2010)
Filesystem volume name: 
Last mounted on: /
Filesystem UUID: 6a49d30a-8aa0-4380-96d3-eb7b2dc33e59
Filesystem magic number: 0xEF53
Filesystem revision #: 1 (dynamic)

df -hT

root@\Barlearn1$ df -hT
Filesystem Type Size Used Avail Use% Mounted on
/dev/xvde ext4 7.8G 1.5G 6.0G 20% /
tmpfs tmpfs 7.3G 0 7.3G 0% /dev/shm

Show that transparent hugepages is disabled
Sysctl -a | grep hugepages
vm.nr_hugepages = 0
vm.nr_hugepages_mempolicy = 0
vm.hugepages_treat_as_movable = 0
vm.nr_overcommit_hugepages = 0

root@\Barlearn1$ pwd
/sys/kernel/mm
root@\Barlearn1$ ls -ltr
total 0
drwxr-xr-x 2 root root 0 Dec 6 02:40 ksm
drwxr-xr-x 3 root root 0 Dec 6 02:40 hugepages

root@\Barlearn1$ cat grub.conf
default=0
timeout=1

title CentOS (2.6.32-642.11.1.el6.x86_64)
root (hd0)
kernel /boot/vmlinuz-2.6.32-642.11.1.el6.x86_64 root=/dev/xvde ro crashkernel=auto LANG=en_US.UTF-8 KEYTABLE=us
initrd /boot/initramfs-2.6.32-642.11.1.el6.x86_64.img
title CentOS-6.3-x86_64-GA-03 2.6.32-279.el6.x86_64
root (hd0)
kernel /boot/vmlinuz-2.6.32-279.el6.x86_64 root=/dev/xvde ro
initrd /boot/initramfs-2.6.32-279.el6.x86_64.img

Report the network interface attributes
cat resolv.conf
cat fstab

Show forward and reverse host lookups using getent and nslookup

getent hosts ip-172-31-10-176 | awk '{print $1}'
172.31.10.176

Nslookup was unavailable

Yum install bind-utils

root@\Barlearn1$ nslookup cloudera.com
Server: 172.31.0.2
Address: 172.31.0.2#53

Non-authoritative answer:
Name: cloudera.com
Address: 74.217.76.7

Verify the nscd service is running
By default the service was missing and I installed using
Yum install nscd
root@\Barlearn1$ service nscd status
nscd (pid 2469) is running...
Verify the ntpd service is running?
Yum install ntp
root@\Barlearn1$ service ntpd status
ntpd (pid 2532) is running...

Service iptables stop
service iptables status

iptables: Firewall is not running.
[root@ip-172-31-10-176 ~]#

Completed !
