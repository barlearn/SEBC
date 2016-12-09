#Region Singapore: ap-southeast-1b

AWS Instances 
AWS Instances

ec2-52-77-224-50.ap-southeast-1.compute.amazonaws.com
ec2-54-179-132-64.ap-southeast-1.compute.amazonaws.com
ec2-52-77-255-32.ap-southeast-1.compute.amazonaws.com
ec2-54-179-161-107.ap-southeast-1.compute.amazonaws.com
ec2-54-169-192-185.ap-southeast-1.compute.amazonaws.com


52.77.224.50
54.179.132.64
52.77.255.32
54.179.161.107
54.169.192.185


172.31.8.31
172.31.2.14
172.31.12.97
172.31.4.150
172.31.15.221


ip-172-31-8-31.ap-southeast-1.compute.internal
ip-172-31-2-14.ap-southeast-1.compute.internal
ip-172-31-12-97.ap-southeast-1.compute.internal
ip-172-31-4-150.ap-southeast-1.compute.internal
ip-172-31-15-221.ap-southeast-1.compute.internal

#operating system
[root@ip-172-31-8-31 ~]# cat /etc/redhat-release
CentOS release 6.5 (Final)


#Disk space

[root@ip-172-31-8-31 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvde        40G  816M   37G   3% /
tmpfs           7.4G     0  7.4G   0% /dev/shm

[root@ip-172-31-15-221 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvde        40G  803M   37G   3% /
tmpfs           7.4G     0  7.4G   0% /dev/shm

[root@ip-172-31-12-97 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvde        40G  803M   37G   3% /
tmpfs           7.4G     0  7.4G   0% /dev/shm

[root@ip-172-31-4-150 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvde        40G  808M   37G   3% /
tmpfs           7.4G     0  7.4G   0% /dev/shm

[root@ip-172-31-2-14 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvde        40G  803M   37G   3% /
tmpfs           7.4G     0  7.4G   0% /dev/shm

#yum repolist 
Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: mirror.vastspace.net
 * extras: mirror.vastspace.net
 * updates: mirror.vastspace.net
repo id                        repo name                                  status
base                           CentOS-6 - Base                            6,696
extras                         CentOS-6 - Extras                             62
updates                        CentOS-6 - Updates                           686
repolist: 7,444

[root@ip-172-31-4-150 ~]# yum repolist
Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: mirror.0x.sg
 * extras: mirror.0x.sg
 * updates: mirror.0x.sg
repo id                        repo name                                  status
base                           CentOS-6 - Base                            6,696
extras                         CentOS-6 - Extras                             62
updates                        CentOS-6 - Updates                           686
repolist: 7,444
[root@ip-172-31-4-150 ~]#

Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: mirror.readyspace.com
 * extras: mirror.readyspace.com
 * updates: mirror.readyspace.com
repo id                        repo name                                  status
base                           CentOS-6 - Base                            6,696
extras                         CentOS-6 - Extras                             62
updates                        CentOS-6 - Updates                           686
repolist: 7,444

Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: mirror.vastspace.net
 * extras: mirror.vastspace.net
 * updates: mirror.vastspace.net
repo id                        repo name                                  status
base                           CentOS-6 - Base                            6,696
extras                         CentOS-6 - Extras                             62
updates                        CentOS-6 - Updates                           686
repolist: 7,444

[root@ip-172-31-8-31 ~]# yum repolist
Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: mirror.0x.sg
 * extras: mirror.0x.sg
 * updates: mirror.0x.sg
repo id                        repo name                                  status
base                           CentOS-6 - Base                            6,696
extras                         CentOS-6 - Extras                             62
updates                        CentOS-6 - Updates                           686
repolist: 7,444

#create users, groups and assignment 
useradd --uid 2700 raffles
useradd --uid 2800 orchard

groupadd shops
groupadd walks

usermod -G shops orchard
usermod -G walks raffles

cat /etc/passwd
raffles:x:2700:2700::/home/raffles:/bin/bash
orchard:x:2800:2800::/home/orchard:/bin/bash

cat /etc/groups
raffles:x:2700:
orchard:x:2800:
shops:x:2801:orchard
walks:x:2802:raffles


