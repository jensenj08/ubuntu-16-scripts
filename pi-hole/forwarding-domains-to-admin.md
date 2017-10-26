# Forwarding domains to /admin
This works with ubuntu 16.04.

In order to get to the admin domain from the root domain automatically. If you want to type <pi-hole-domain> and be redirected to <pi-hole-domain>/admin, this is how you do it.

### Prerequisites
You need to have a DNS server, or entries in your local hosts file which will forward the host that you're using to the domian of the pi-hole.

## Create new web config for server
```
sudo nano /etc/lighttpd/external.conf
```

Just create a redirect section. If you have more than one domain that you
would like to redirect, just repeat this code block as many times as you want.
Replace <pi-hole-domain> with the domain that you have being forwarded to the server.
```
# Entering just "<pi-hole-domain>" into a browser redirects to "pi.hole/admin/"
$HTTP["host"] == "<pi-hole-domain>" {
    $HTTP["url"] == "/" {
        url.redirect = ( "" => "/admin/" )
    }
}
```
Once this is complete, restart the server.
```
sudo service lighttpd restart
```
