# Network Services Delegations

I currently use an [Ubiquiti EgdeRouter Lite][erl_amazon] (ERL) as the firewall
and NAT gateway to the world, with future plans to move to a [PC Engines
APU][pce_apu]. Once I get the APU, I will probably keep the ERL around as an
NSD server to the local LAN.

## Router

The main router is in charge of serveral tasks:

 * [pf(4)](http://man.openbsd.org/pf) NAT gateway
   ([see also](https://www.openbsd.org/faq/pf/example1.html#pf))
 * Primary DHCP server
 * Primary DNS server ([unbound(8)](http://man.openbsd.org/unbound)) combined
   with [DNSCrypt](https://dnscrypt.org/)
 * VPN server for my cell phone



[erl_amazon]:		https://www.amazon.com/Ubiquiti-Edgerouter-ERLITE-3-Desktop-Router/dp/B00HXT8EKE/
[pce_apu]:		http://www.pcengines.ch/apu2.htm/
