# OpenBSD on the EdgeRouter Lite

 - [Fresh Install](#fresh-install)
 - [Upgrading](#upgrading-openbsd-on-erl)

## Fresh Install

#### Related Posts

There are already a few articles with installation instructions for various
operating systems, certainly enough to get you going.

 * http://www.tedunangst.com/flak/post/OpenBSD-on-ERL ([cached][ted-erl-cached])
 * http://www.daemonology.net/blog/2016-01-10-FreeBSD-EdgeRouter-Lite.html ([cached][collin-erl-cached])
 * http://rtfm.net/FreeBSD/ERL/ ([cached][rtfm-erl-cached])
 * https://wiki.gentoo.org/wiki/MIPS/ERLite-3 ([cached][gentoo-erl-cached])

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

## Upgrading OpenBSD on ERL

XXX: stub



[erl_amazon]:			https://www.amazon.com/Ubiquiti-Edgerouter-ERLITE-3-Desktop-Router/dp/B00HXT8EKE/
[serial_amazon]:		https://www.amazon.com/Generic-7-Cisco-Console-RJ45-to-DB9/dp/B000GL3MOY/
[ted-erl-cached]:		https://web.archive.org/web/20170107022914/http://www.tedunangst.com/flak/post/OpenBSD-on-ERL/
[collin-erl-cached]:	https://web.archive.org/web/20161022145524/http://www.daemonology.net/blog/2016-01-10-FreeBSD-EdgeRouter-Lite.html
[rtfm-erl-cached]:		https://web.archive.org/web/20160822180531/http://rtfm.net/FreeBSD/ERL/
[gentoo-erl-cached]:	https://web.archive.org/web/20151003175724/https://wiki.gentoo.org/wiki/MIPS/ERLite-3
