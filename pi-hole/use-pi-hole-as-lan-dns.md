# Use pi hole as lan dns

https://discourse.pi-hole.net/t/howto-using-pi-hole-as-lan-dns-server/533

With a little configuration, you can use your pi-hole as the DNS server for your LAN, if, for example, your router isn't doing a very good job serving local names. Here's how:

## Create a new config file
Create a new dnsmasq configuration file called
/etc/dnsmasq.d/02-lan.conf:
```
sudo touch /etc/dnsmasq.d/02-lan.conf
```
Go into the file you just created:
```
sudo nano /etc/dnsmasq.d/02-lan.conf
```
Add the following to the file.
You can replace /lan/ with whatever you want
your network domain to be. For example,
you could put it as /com/ but you wouldn't be able to
got to any .com websites if you did this. Fuck you, right?!
```
local=/lan/
addn-hosts=/etc/pihole/lan.list
```
After this, create a "hosts file" for your network /etc/pihole/lan.list with the format ipaddress fqdn hostname.
If you want to, you can just add the fqdn (fully qualified domain name).
```
192.168.1.40     marvin.your.lan  marvin
192.168.1.41     fucking.lan
192.168.1.42     hactar.your.lan  hactar
```
Substitute "your.lan" for whatever you want your domain name to be.

On your DHCP server (most likely your router, though pi-hole indeed can be configured into one), you'll also need to set your search domain to whatever "your.lan" corresponds to.

Finally, restart your name server:
```
sudo service dnsmasq force-reload
```
