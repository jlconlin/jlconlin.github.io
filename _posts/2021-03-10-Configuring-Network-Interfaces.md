---
title: Configuring Network Interfaces
date: 2021-03-10 06:20
tags: 
  - network
  - virtual interface
  - config
---
In trying to get pi-hole working at home, I need to have multiple IP addresses for my Raspberry Pi server. I need this because my router requires three different IP addresses.

You can create a virtual network interface *temporarily* by executing the command:
{% highlight console %}
ifconfig eth0:0 <new IP address>
{% endhighlight %}

If you want to *permanently* do the above you need to modify two files `/etc/network interfaces` and `/etc/dhcpcd.conf`. [^Raspbian] The example below are to add two virtual interfaces.

**`/etc/network/interfaces`**
{% highlight txt %}
# VLan 1 Interface
auto eth0.1
iface eth0.1 inet manual
  vlan-raw-device eth0

auto eth0.2
iface eth0.2 inet manual
  vlan-raw-device eth0

{% endhighlight %}

**`/etc/dhcpcd.conf`**
{% highlight txt %}
# Leave physical interface alone
denyinterfaces eth0

# Static IP configuration for VLan 1 and 2
interface eth0.1
  static ip_address=<new IP address>
  static routers=<IP address for router>
  static domain_name_servers=<DNS IP address>

interface eth0.2
  static ip_address=<second new IP address>
{% endhighlight %}

After you make these changes, you'll have to reboot.

This worked mostly well for me. For some reason the second virtual interface didn't quite take. I'm not sure why.

I learned all of this from the [forums](https://www.raspberrypi.org/forums/viewtopic.php?p=998957#p998957) on <https://www.raspberrypi.org/forms>.
[^Raspbian]: I am doing this with the Raspbian OS, so this may be different in other circumstances

