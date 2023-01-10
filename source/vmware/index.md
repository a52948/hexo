---
date: date
title: centos9 安装vmwork station 17.0
updated: 2023-01-10 13:25:13
---
需要编译安装vmmon


#git clone https://github.com/mkubecek/vmware-host-modules

# cd vmware-host-modules

#git  branch -a

#remotes/origin/master
remotes/origin/player
remotes/origin/player-12.5.2
remotes/origin/player-12.5.5
remotes/origin/player-12.5.6
查看本机的vmware

vmware --version
VMware Workstation 16.2.1 build-18811642

执行

git checkout workstation-17.0

开始编译安装后

 make

make  install


然后加载vmware的虚拟网卡模块：

```
modprobe vmnet vmw_vmci vmmon
```


再查看是否能够正常启动网络：

```csharp
# vmware-networks --start
Started Bridge networking on vmnet0
Enabled hostonly virtual adapter on vmnet1
Started DHCP service on vmnet1
Started NAT service on vmnet8
Enabled hostonly virtual adapter on vmnet8
Started DHCP service on vmnet8
Started all configured services on all networks
```
