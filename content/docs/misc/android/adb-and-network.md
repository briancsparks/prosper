---
title: "ADB and Network"
description: "ADB The Android"
date: 2020-04-12T02:12:44-07:00
draft: false
---

### Logcat

Logcat command to get all the buffers, with best info.

```sh
adb logcat -v threadtime -v epoch -v uid -v usec -b all -d
```

Drop the `-d` to keep the log running indefinately.

```sh
adb logcat -v threadtime -v epoch -v uid -v usec -b all
```

### Get Android's IP address

Get link-layer info:

```sh
ip link
```

Which output something the following. Note the lack of IP addresses.

```sh
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: bond0: <BROADCAST,MULTICAST,MASTER> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether fe:b6:71:01:d8:27 brd ff:ff:ff:ff:ff:ff
3: dummy0: <BROADCAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/ether 22:b9:0d:2b:e5:09 brd ff:ff:ff:ff:ff:ff
4: ip_vti0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN mode DEFAULT group default qlen 1
    link/ipip 0.0.0.0 brd 0.0.0.0
5: ip6_vti0@NONE: <NOARP> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1
    link/tunnel6 :: brd ::
6: sit0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN mode DEFAULT group default qlen 1
    link/sit 0.0.0.0 brd 0.0.0.0
7: ip6tnl0@NONE: <NOARP> mtu 1452 qdisc noop state DOWN mode DEFAULT group default qlen 1
    link/tunnel6 :: brd ::
8: rmnet_ipa0: <UP,LOWER_UP> mtu 2000 qdisc pfifo_fast state UNKNOWN mode DEFAULT group default qlen 1000
    link/[530]
9: rmnet_data0: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
10: rmnet_data1: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
11: rmnet_data2: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
12: rmnet_data3: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
13: rmnet_data4: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
14: rmnet_data5: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
15: rmnet_data6: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
16: rmnet_data7: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
17: r_rmnet_data0: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
18: r_rmnet_data1: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
19: r_rmnet_data2: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
20: r_rmnet_data3: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
21: r_rmnet_data4: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
22: r_rmnet_data5: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
23: r_rmnet_data6: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
24: r_rmnet_data7: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
25: r_rmnet_data8: <> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/[530]
26: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 3000
    link/ether 40:4e:36:93:9a:78 brd ff:ff:ff:ff:ff:ff
27: p2p0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN mode DEFAULT group default qlen 3000
    link/ether 42:4e:36:93:9a:78 brd ff:ff:ff:ff:ff:ff
```

Once you have the name of the interface, get other info:

```sh
ip addr show wlan0
```

Which output something like this. I got `wlan0`, `lo`, an IPv6 from `dummy0`.

```sh
26: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 3000
    link/ether 40:4e:36:93:9a:78 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.11/24 brd 192.168.1.255 scope global wlan0
       valid_lft forever preferred_lft forever
    inet6 fe80::424e:36ff:fe93:9a78/64 scope link
       valid_lft forever preferred_lft forever
```

### Other Commands in adb shell

```sh
ip ntable
ip rotue      # shows ip address
ip neigh      # Shows IP and MAC of LAN neighbors
ip maddress   # MACs and a few IPs of ifaces
ip netconf
netstat

```
