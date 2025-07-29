# GNSS-Lab
Various receiver equipment for GNSS lab experiments

## Configured Equipment

* alidade (198.19.250.201), PC Engines APU, 2x MC7455 
* barometer (198.19.250.201), *offline, not installed yet*, PC Engines 1x RM500.
* kamal (198.19.250.211), Celerway Arcus, 2x RM505Q-AE, 1x BG 96 (IoT) + Build in receiver - Note: Jan is not sure if GPS is available on the BG 96 module - there is one empty mounting base for a connector on the PCB.

## Accessing Lab

A VPN gateway or jump host must be used to connect to the equipment. 

* Accessing the SSH-Jumphost requires an active OpenVPN connection from SimulaMet CRNA
* Management IP-Range is 198.19.250.0/24 (RFC 2544)

### Webinterface

To access the webinterface, forward ports 443/tcp and 80/tcp. It is - in this example - accessible at http://localhost:8081 and https://localhost:4431

`ssh -L 4431:localhost:443 -L 8081:localhost:80 kamal.gnss.dev`

### Wireguard / VPN

Send your public key (use `wg gen-key` and `wg pubkey`) to Jan, receive an IP-address in return. Configuration will look like this:

```
[Interface]
ListenPort = 41210 # Choose at will
PrivateKey = <secret key>

[Peer]
PublicKey = rotbOEGktIN/amXF/T96sETXl4iG197YnA+1Dzsz634=
AllowedIPs = 198.19.250.0/24
Endpoint = vpn.gnss.dev:10020
PersistentKeepalive = 15
```

### SSH Jumphost

Ask Jan for an account on the jumphost. Have an `.ssh/config` entry like this:
``` 
Host ssh.gnss.dev
  HostName ssh.gnss.dev
  User <your username for the jumphost>

Host alidade.gnss.dev
  HostName alidade.gnss.dev
  ProxyJump ssh.gnss.dev
  User root

Host barometer.gnss.dev
  HostName barometer.gnss.dev
  ProxyJump ssh.gnss.dev
  User root

Host kamal.gnss.dev
  HostName kamal.gnss.dev
  ProxyJump  ssh.gnss.dev
  User root
```


