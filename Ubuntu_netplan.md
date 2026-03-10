# Quick notes on how to work with Canonial Netplan

### Reference Resources
- [Official page](https://netplan.io/)
- [Readthedocs page](https://netplan.readthedocs.io/)
- [Github page](https://github.com/canonical/netplan)

### Netplan CLI
**IMPORTANT**
- Run `netplan apply` to apply all changes made by `netplan set` command
- Reboot the machine after issuing `netplan apply` and check if the new settings/changes are persistent

**USAGE**
- `netplan apply` - apply configuration from Netplan YAML files to a running system
- `netplan get` - reads all YAML files from `/{etc,lib,run}/netplan/*.yaml` and returns a merged view of the current configuration.
  
  The below outputs show that there are three `.yaml` files (`40-air.yaml`, `50-cloud-init.yaml` and `70-netplan-set.yaml`) in `/etc/netplan/` folder. Each file has different content. The `netplan get` returns a merged view of all of them:
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
- `netplan set` writes a given key/value pair or YAML subtree into a YAML file from `/{etc,lib,run}/netplan/` and validates its format.

  - *Example 1*: To disable DHCPv4 and DHCPv6 on interface `eth0`:
    ```
    ubuntu@ubuntu:~$ sudo netplan set ethernets.eth0.dhcp4=false
    ubuntu@ubuntu:~$ sudo netplan set ethernets.eth0.dhcp6=false
    ```
  - *Example 2*: To set an IPv4 address of `192.168.0.11` with subnet mask `255.255.255.0` (or `192.168.0.11/24`) for interface `eth1`:
    ```
    ubuntu@ubuntu:~$ sudo netplan set "ethernets.eth1.addresses=[192.168.0.11/24]"
    ```
  - *Example 3*: To create a sub-interface `eth0.100` (vlan id 100, or dot1q tag 100 under interface `eth0`), then assign an IP address of `10.0.100.10` with subnet mask `255.255.255.0` (or `10.0.100.10/24`) to it.
    
    Bear in mind that we must use the `\.` to escapte the character `.` used to define the sub-interface `eth0.100` so that Bash Shell understands and takes them as a whole: 
    ```
    ubuntu@ubuntu:~$ sudo netplan set "vlans.eth0\.100={id: 100, link: eth0}"
    ubuntu@ubuntu:~$ sudo netplan set "vlans.eth0\.100.addresses=[10.0.100.10/24]"
    ``` 
  - *Example 4*: To create three VRFs:
    - VRF#1: vrf name `app-100` and table id `100`
    - VRF#2: vrf name `app-200` and table id `200`
    - VRF#3: vrf name `app-300` and table id `300`
    ```
    ubuntu@Ubuntu:~$ sudo netplan set "vrfs.app-100.table=100"
    ubuntu@Ubuntu:~$ sudo netplan set "vrfs.app-200.table=200"
    ubuntu@Ubuntu:~$ sudo netplan set "vrfs.app-300.table=300"
    ```
     - Verify if all new configurations are correctly written to netplan `*.yaml` files:
    ```
    ubuntu@ubuntu:~$ sudo netplan get
    <output omitted>
    vrfs:
      app-100:
        table: 100
      app-200:
        table: 200
      app-300:
        table: 300
    ubuntu@ubuntu:~$
    ```
    
