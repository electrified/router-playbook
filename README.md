Debian 11 / bullseye / stable

Build image with debian image builder
Set 1 eth to have static ip
run ansible


```
ansible-galaxy install -r requirements.yml
ansible-playbook -l nanopi -u ed -k -e @secrets_file.enc --ask-vault-pass playbook.yml
ansible-playbook -l nanopi -u ed2 -e @secrets_file.enc --ask-vault-pass playbook.yml 
```

Interface ordering fix
https://github.com/pyavitz/debian-image-builder/issues/40

MTU info
https://www.sonicwall.com/support/knowledge-base/how-can-i-optimize-pppoe-connections/170505851231244/

## DNS resolution
/etc/resolvconf/update.d/dnsmasq causes the DNS servers to be written to /run/dnsmasq/resolv.conf 

## IPv6 info

### Services and their purpose
- Radvd -Router Advertisement
- dnsmasq - internal dhcp, dns
- dhcpcd5

https://wiki.debian.org/IPv6PrefixDelegation
https://wiki.archlinux.org/title/IPv6

https://askubuntu.com/questions/56890/ipv6-over-pppoe
https://bbs.archlinux.org/viewtopic.php?id=244241

https://www.reddit.com/r/ipv6/comments/deb531/linux_xfinity_dhcpcd_and_getting_a_local_prefix/

https://vk5tu.livejournal.com/37206.html

https://wiki.gentoo.org/wiki/IPv6_router_guide

## DHCPv6 clients

dhcpcd5 https://roy.marples.name/git/dhcpcd Debian version is well out of date

dhcpcd -f /etc/dhcpcd.conf.new -dB


wide-dhcpv6-client - https://github.com/opnsense/dhcp6c looks a bit unmaintained, and especially unmaintained in Debian

isc-dhcp-client - https://www.isc.org/dhcp/ Installed in Debian by default however "ISC has ended development on the ISC DHCP client as of early 2022. This client implementation is no longer maintained and should not be used in production any longer."

https://radvd.litech.org/

https://github.com/systemd/systemd/issues/481

## IPv6 Debugging
`ping -6 google.com`
`ip -6 route`
`ping ipv6.google.com`

https://ipv6-test.com/
https://test-ipv6.com/

Show routing table `ip -6 route show` or `netstat -rn -6`

Doing a `systemctl restart dhcpcd` temporarily improves the ipv6 situation, however it breaks again after restarting pppoe. It can be seen from looking at the ipv6 routing table there is no default route.

wide-dhcpv6-client has been installed manually - uninstall - done