# Use pi hole as lan dns

https://discourse.pi-hole.net/t/howto-using-pi-hole-as-lan-dns-server/533

I basically ripped the info out of the above link and changed it a little... thanks for the post llauren.

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
got to any .com websites if you did this. That would be bad, right?!
```
local=/lan/
addn-hosts=/etc/pihole/lan.list
```
If you wanted to tell a host to use a local address for a internet domain such as... facebook, you could so something like:
```
local=/facebook.com/
```

Maybe you can put up a page telling your grandparents that they've spend enough time on facebook instead of displaying the regular message.
To do that, you would need to assign a local ip address to the your lan.list file.

Or if you want the local dmn to assume that all .com website were on your local lan, you could put:
```
local=/com/
```
You can have as many as these local rules in your file as you want, but just remember, the more you have, the more you have to maintain. 

## List your hosts
After this, create a "hosts file" for your network /etc/pihole/lan.list with the format ipaddress fqdn hostname.
If you want to, you can just add the fqdn (fully qualified domain name).
```
192.168.1.40     marvin.your.lan  marvin
192.168.1.41     another-box.lan
192.168.1.42     hactar.your.lan  hactar
```
Substitute "your.lan" for whatever you want your domain name to be.

## Restart service
Finally, restart your name server:
```
sudo service dnsmasq force-reload
```
It should work after this, so if it doesn't, you're kind of hosed. It'd be time to debug.
