# safe-dnsmasq
Config settings to avoid porn and other bits while on your local network

Currently the setup uses OpenDNS to block inappropriate website, but also uses
safe versions of search engines such as

* Google
* Bing
* Youtube
* DuckDuckGo
* Yandex [1][section-yandex]

# Requirements
You will need a network device that can run dnsmasq available and have dnsmasq installed

# Setup
edit /etc/dnsmasq.conf, look for and uncomment the following lines:
```
no-resolv
conf-dir=/etc/dnsmasq.d/,*.conf
```

## /etc/hosts
Append from the hosts file in the repo to that of your hosts file
```
curl -s https://raw.githubusercontent.com/EldonMcGuinness/dnsmasq-safenet/master/hosts >> /etc/hosts
```

## /etc/dnsmasq.d/safenet.conf
Download the latest rules to redirect unprotected urls to protected ones
```
curl -s https://raw.githubusercontent.com/EldonMcGuinness/dnsmasq-safenet/master/safenet.conf > /etc/dnsmasq.d/safenet.conf

```

## Finishing up
At this point you will want to restart/reload dnsmasq and wait a few moments for the changes to take affect.


# Issues

###### Yandex Issues
Yandex does not offer an official way to filter out inappropriate images from being shown
so instead I redirect these image urls to the localhost (127.0.0.1)

[section-yandex]: #yandex-issues 
