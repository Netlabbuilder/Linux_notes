# Quick notes on how to work with Canonial Netplan

#### Reference Resources
- [Official page](https://netplan.io/)
- [Readthedocs page](https://netplan.readthedocs.io/)
- [Github page](https://github.com/canonical/netplan)

#### Netplan CLI
- `netplan get` - reads all YAML files from /{etc,lib,run}/netplan/*.yaml and returns a merged view of the current configuration.
  
  The below outputs show that there are three `.yaml` files, each has different content. The `netplan get` returns a merged view of all of them:
  ```
  ubuntu@ubuntu:~$ ls -l /etc/netplan/
  total 12
  -rw------- 1 root root  43 Mar  8 11:25 40-air.yaml
  -rw------- 1 root root 180 Mar  8 11:25 50-cloud-init.yaml
  -rw------- 1 root root 244 Mar  8 11:27 70-netplan-set.yaml
  ubuntu@ubuntu:~$ sudo cat /etc/netplan/40-air.yaml
  network:
    version: 2
    renderer: networkd
  ubuntu@ubuntu:~$ 
  ubuntu@ubuntu:~$ sudo cat /etc/netplan/50-cloud-init.yaml
  network:
    version: 2
    ethernets:
      eth0:
        match:
          name: "eth0"
          macaddress: "48:b0:2d:2e:7e:8d"
        dhcp4: false
        dhcp6: false
        set-name: "eth0"
  ubuntu@ubuntu:~$ sudo cat /etc/netplan/70-netplan-set.yaml 
  network:
    version: 2
    ethernets:
      eth1:
        addresses:
        - "192.168.0.11/24"
    vlans:
      eth0.100:
        addresses:
        - "10.0.100.10/24"
        id: 100
        link: "eth0"
        routes:
        - to: default
          via: 10.0.100.1
  ubuntu@ubuntu:~$ sudo netplan get
  network:
    version: 2
    renderer: networkd
    ethernets:
      eth0:
        match:
          name: "eth0"
          macaddress: "48:b0:2d:2e:7e:8d"
        dhcp4: false
        dhcp6: false
        set-name: "eth0"
      eth1:
        addresses:
        - "192.168.0.11/24"
    vlans:
      eth0.100:
        addresses:
        - "10.0.100.10/24"
        routes:
        - to: "default"
          via: "10.0.100.1"
        id: 100
        link: "eth0"
  ubuntu@ubuntu:~$
  ```
