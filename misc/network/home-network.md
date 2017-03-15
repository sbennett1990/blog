# Home Network Design

I primarily use OpenBSD on my router/servers to provide the core services to my
home network. This writeup is a combination of step-by-step instructions to get
everything up and running and an information dump. Your mileage may vary.

## Router

My main router is in charge of serveral tasks:

 * [pf(4)](http://man.openbsd.org/pf) NAT gateway (also [here](obsd_pf_guide))
 * Primary DHCP server
 * Primary DNS server ([unbound(8)](http://man.openbsd.org/unbound)) combined
   with [DNSCrypt](https://dnscrypt.org/)
 * VPN server for my cell phone

I currently use an [Ubiquiti EgdeRouter Lite][erl_amazon] (ERL) as the firewall
and NAT-gateway to the world, with future plans to move to PCEngine's APU. Once
I get the APU, I will probably keep the ERL around as an NSD server to the
local LAN.

### Installing OpenBSD on EdgeRouter Lite

#### Related Posts

There are already a few articles with installation instructions for various
operating systems, certainly enough to get you going.

 * http://www.tedunangst.com/flak/post/OpenBSD-on-ERL
 * http://www.daemonology.net/blog/2016-01-10-FreeBSD-EdgeRouter-Lite.html
 * http://rtfm.net/FreeBSD/ERL/
 * https://wiki.gentoo.org/wiki/MIPS/ERLite-3

#### Required

 * EgdeRouter Lite
 * Low profile USB flash drive
 * Small Phillps screwdriver
 * Another system with DHCP, tftpd, and a Serial port
 * Serial cable ([like this one][serial_amazon])

#### Steps

1. Set up a DHCP and tftpd server

The ERL will have to boot the install image over the network, which means it
will need DHCP and an accessible tftpd server. In other words, you need a
second computer (preferrably running OpenBSD).

2. Put the octeon `bsd.rd` file in `/tftproot`

3. Replace the internal USB drive

The stock internal storage is very small (4GB) and fairly cheap quality. Replace
with something larger. The USB drive must be very low profile to fit in the
case! I used a [32GB SanDisk Cruzer Fit](https://www.amazon.com/dp/B00812F7O8/).

4. Connect to the ERL over the serial port

On OpenBSD, the command would be (as root):

```
# cu -l /dev/cuaU0 -s 115200
```



[erl_amazon]:		https://www.amazon.com/Ubiquiti-Edgerouter-ERLITE-3-Desktop-Router/dp/B00HXT8EKE/
[serial_amazon]:	https://www.amazon.com/Generic-7-Cisco-Console-RJ45-to-DB9/dp/B000GL3MOY/
[obsd_pf_guide]:	https://www.openbsd.org/faq/pf/example1.html#pf
