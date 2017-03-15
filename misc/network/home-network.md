# Home Network Design

I primarily use OpenBSD on my router/servers to provide the core services to my
home network. This writeup is a combination of step-by-step instructions to get
everything up and running and an information dump. Your mileage may vary.

## Router

I currently use an Ubiquiti EgdeRouter Lite (ERL) as the firewall and
NAT-gateway to the world, with future plans to move to PCEngine's APU. Once I
get the APU, I will probably keep the ERL around as an NSD server to the local
LAN.

There are already a few articles with installation instructions for various
operating systems, certainly enough to get you going. Here are my steps:

### Installation Steps

1. Set up a DHCP and tftpd server

The ERL will have to boot the install image over the network, which means it
will need DHCP and an accessible tftpd server. In other words, you need a
second computer (preferrably running OpenBSD).

2. Put the octeon *bsd.rd* file in */tftproot*

3. Replace the internal USB drive

The stock inernal storage is very small (4GB) and fairly cheap quality. Replace
with something larger. The USB drive must be very low profile to fit in the
case! I used a (32GB SanDisk Cruzer Fit)[https://www.amazon.com/dp/B00812F7O8/].

4. Connect to the ERL over the serial port

On OpenBSD, the command would be (as root):

```
# cu -l /dev/cuaU0 -s 115200
```
