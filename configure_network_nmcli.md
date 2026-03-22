**IMPORTANT NOTE**\
The `ip address add` command is to temporarily set an IP address on a network interface.\
This means the result of `ip address add` command, and also the results of other `ip` commands are non-persistent. They will be lost after the system is rebooted.\

Please use **nmcli** or **nmtui** to make the network configuration persistent!

Below are examples of using **nmcli** to configure network changes:
- To list current connections, use `nmcli conn show`
  ```
  $ nmcli conn show
  NAME        UUID                                  TYPE      DEVICE
  ens33.100   c4ac41ec-00f2-45e1-9add-7cad6c8c249f  vlan      ens33.100
  ens33       1f331b44-372a-31dc-b62e-060a25a6f40f  ethernet  ens33
  lo          416702f3-6d6d-4354-a422-99797abda818  loopback  lo
  ```
- To list current devices, use `nmcli device show`
  ```
  $ nmcli device show
  GENERAL.DEVICE:                         ens33.100
  GENERAL.TYPE:                           vlan
  GENERAL.HWADDR:                         00:50:56:04:08:60
  GENERAL.MTU:                            1500
  GENERAL.STATE:                          100 (connected)
  GENERAL.CONNECTION:                     ens33.100
  GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/419
  IP4.ADDRESS[1]:                         192.168.56.11/24
  IP4.GATEWAY:                            192.168.56.1
  IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 10.106.35.97, mt = 400
  IP4.ROUTE[2]:                           dst = 10.106.35.96/28, nh = 0.0.0.0, mt = 400
  IP6.ADDRESS[1]:                         fe80::72a:1413:609c:8f78/64
  IP6.GATEWAY:                            --
  IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 1024
  
  GENERAL.DEVICE:                         lo
  GENERAL.TYPE:                           loopback
  GENERAL.HWADDR:                         00:00:00:00:00:00
  GENERAL.MTU:                            65536
  GENERAL.STATE:                          100 (connected (externally))
  GENERAL.CONNECTION:                     lo
  GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
  IP4.ADDRESS[1]:                         127.0.0.1/8
  IP4.GATEWAY:                            --
  IP6.ADDRESS[1]:                         ::1/128
  IP6.GATEWAY:                            --
  
  GENERAL.DEVICE:                         ens33
  GENERAL.TYPE:                           ethernet
  GENERAL.HWADDR:                         00:50:56:04:08:60
  GENERAL.MTU:                            1500
  GENERAL.STATE:                          30 (disconnected)
  GENERAL.CONNECTION:                     --
  GENERAL.CON-PATH:                       --
  WIRED-PROPERTIES.CARRIER:               on
  IP4.GATEWAY:                            --
  IP6.GATEWAY:                            --
  ```

- To make configuration changes (DHCP  method: auto or manual, ip address, gateway, dns ...) on a connection, use `nmcli connection modify`:
  ```
  $ nmcli connection modify ens33 ipv4.method manual ipv4.address 192.168.56.11/24 ipv4.gateway 192.168.56.1
  ```
- To apply new changes, bring the connection `down` and `up`
  ```
  $ sudo nmcli connection down ens33
  $ sudo nmcli connection up ens33
  ```
- To verify the changes:
  ```
  nmcli
  nmcli device status
  nmcli device show
  nmcli connection show
  ```
- Last but not lease, for the first network changes, reboot the machine and confirm that the network changes are persistent.
