# iptables rules for unifi controller

Example rules when running a containerized unifi controller such as https://hub.docker.com/r/jacobalberty/unifi/ on docker. Following example rule only allows packets originating from the net `192.168.192.0/24` to the selected ports.

See https://help.ui.com/hc/en-us/articles/218506997-UniFi-Ports-Used for a complete list of ports used by the controller.

```bash
iptables -I DOCKER-USER -p tcp  -m multiport --dports 8443,8080,3478 ! -s 192.168.192.0/24 -j DROP
iptables -I DOCKER-USER -p udp  -m multiport --dports 8443,8080,3478 ! -s 192.168.192.0/24 -j DROP
```