---
abbrlink: ''
categories: []
date: '2023-04-23 17:20:05'
tags: []
title: zerotier
updated: '2023-04-23 17:26:48'
---

zerotier 路由旁路的实验，在跳板机上操作如下

```
[root@localhost ~]# vi /etc/sysctl.conf
# sysctl settings are defined through files in
# /usr/lib/sysctl.d/, /run/sysctl.d/, and /etc/sysctl.d/.
#
# Vendors settings live in /usr/lib/sysctl.d/.
# To override a whole file, create a new file with the same in
# /etc/sysctl.d/ and put new settings there. To override
# only specific settings, add a file with a lexically later
# name in /etc/sysctl.d/ and put new settings there.
#
# For more information, see sysctl.conf(5) and sysctl.d(5).
net.ipv4.ip_forward = 1
net.ipv4.conf.all.proxy_arp = 1

[root@localhost ~]#sysctl -p /etc/sysctl.conf

[root@localhost ~]#firewall-cmd --permanent --zone=internal --change-interface=zttyxavm2z

[root@localhost ~]#firewall-cmd --permanent --direct --passthrough ipv4 -t nat POSTROUTING -o ens32 -j MASQUERADE -s 10.11.12.0/24

firewall-cmd --reload

```
