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
- To list all details of a connection, use `nmcli conn show <connection_name>`
  ```
  $ nmcli conn show ens33.100
  connection.id:                          ens33.100
  connection.uuid:                        c4ac41ec-00f2-45e1-9add-7cad6c8c249f
  connection.stable-id:                   --
  connection.type:                        vlan
  connection.interface-name:              --
  connection.autoconnect:                 yes
  connection.autoconnect-priority:        0
  connection.autoconnect-retries:         -1 (default)
  connection.multi-connect:               0 (default)
  connection.auth-retries:                -1
  connection.timestamp:                   1774185233
  connection.permissions:                 --
  connection.zone:                        --
  connection.controller:                  --
  connection.master:                      --
  connection.slave-type:                  --
  connection.port-type:                   --
  connection.autoconnect-slaves:          -1 (default)
  connection.autoconnect-ports:           -1 (default)
  connection.down-on-poweroff:            -1 (default)
  connection.secondaries:                 --
  connection.gateway-ping-timeout:        0
  connection.ip-ping-timeout:             0
  connection.ip-ping-addresses:           --
  connection.ip-ping-addresses-require-all:-1 (default)
  connection.metered:                     unknown
  connection.lldp:                        default
  connection.mdns:                        -1 (default)
  connection.llmnr:                       -1 (default)
  connection.dns-over-tls:                -1 (default)
  connection.mptcp-flags:                 0x0 (default)
  connection.wait-device-timeout:         -1
  connection.wait-activation-delay:       -1
  802-3-ethernet.port:                    --
  802-3-ethernet.speed:                   0
  802-3-ethernet.duplex:                  --
  802-3-ethernet.auto-negotiate:          no
  802-3-ethernet.mac-address:             --
  802-3-ethernet.cloned-mac-address:      --
  802-3-ethernet.generate-mac-address-mask:--
  802-3-ethernet.mac-address-denylist:    --
  802-3-ethernet.mtu:                     auto
  802-3-ethernet.s390-subchannels:        --
  802-3-ethernet.s390-nettype:            --
  802-3-ethernet.s390-options:            --
  802-3-ethernet.wake-on-lan:             default
  802-3-ethernet.wake-on-lan-password:    --
  802-3-ethernet.accept-all-mac-addresses:-1 (default)
  ipv4.method:                            manual
  ipv4.dns:                               --
  ipv4.dns-search:                        --
  ipv4.dns-options:                       --
  ipv4.dns-priority:                      0
  ipv4.addresses:                         192.168.56.11/24
  ipv4.gateway:                           192.168.56.1
  ipv4.routes:                            --
  ipv4.route-metric:                      -1
  ipv4.route-table:                       0 (unspec)
  ipv4.routing-rules:                     --
  ipv4.replace-local-rule:                -1 (default)
  ipv4.dhcp-send-release:                 -1 (default)
  ipv4.routed-dns:                        -1 (default)
  ipv4.ignore-auto-routes:                no
  ipv4.ignore-auto-dns:                   no
  ipv4.dhcp-client-id:                    --
  ipv4.dhcp-iaid:                         --
  ipv4.dhcp-dscp:                         --
  ipv4.dhcp-timeout:                      0 (default)
  ipv4.dhcp-send-hostname-deprecated:     yes
  ipv4.dhcp-send-hostname:                -1 (default)
  ipv4.forwarding:                        -1 (default)
  ipv4.dhcp-hostname:                     --
  ipv4.dhcp-fqdn:                         --
  ipv4.dhcp-hostname-flags:               0x0 (none)
  ipv4.never-default:                     no
  ipv4.may-fail:                          yes
  ipv4.required-timeout:                  -1 (default)
  ipv4.dad-timeout:                       -1 (default)
  ipv4.dhcp-vendor-class-identifier:      --
  ipv4.dhcp-ipv6-only-preferred:          -1 (default)
  ipv4.link-local:                        0 (default)
  ipv4.dhcp-reject-servers:               --
  ipv4.auto-route-ext-gw:                 -1 (default)
  ipv4.shared-dhcp-range:                 --
  ipv4.shared-dhcp-lease-time:            0 (default)
  ipv6.method:                            auto
  ipv6.dns:                               --
  ipv6.dns-search:                        --
  ipv6.dns-options:                       --
  ipv6.dns-priority:                      0
  ipv6.addresses:                         --
  ipv6.gateway:                           --
  ipv6.routes:                            --
  ipv6.route-metric:                      -1
  ipv6.route-table:                       0 (unspec)
  ipv6.routing-rules:                     --
  ipv6.replace-local-rule:                -1 (default)
  ipv6.dhcp-send-release:                 -1 (default)
  ipv6.routed-dns:                        -1 (default)
  ipv6.ignore-auto-routes:                no
  ipv6.ignore-auto-dns:                   no
  ipv6.never-default:                     no
  ipv6.may-fail:                          yes
  ipv6.required-timeout:                  -1 (default)
  ipv6.ip6-privacy:                       -1 (default)
  ipv6.temp-valid-lifetime:               0 (default)
  ipv6.temp-preferred-lifetime:           0 (default)
  ipv6.addr-gen-mode:                     default
  ipv6.ra-timeout:                        0 (default)
  ipv6.mtu:                               auto
  ipv6.dhcp-pd-hint:                      --
  ipv6.dhcp-duid:                         --
  ipv6.dhcp-iaid:                         --
  ipv6.dhcp-timeout:                      0 (default)
  ipv6.dhcp-send-hostname-deprecated:     yes
  ipv6.dhcp-send-hostname:                -1 (default)
  ipv6.dhcp-hostname:                     --
  ipv6.dhcp-hostname-flags:               0x0 (none)
  ipv6.auto-route-ext-gw:                 -1 (default)
  ipv6.token:                             --
  vlan.parent:                            ens33
  vlan.id:                                100
  vlan.flags:                             1 (REORDER_HEADERS)
  vlan.protocol:                          --
  vlan.ingress-priority-map:              --
  vlan.egress-priority-map:               --
  proxy.method:                           none
  proxy.browser-only:                     no
  proxy.pac-url:                          --
  proxy.pac-script:                       --
  GENERAL.NAME:                           ens33.100
  GENERAL.UUID:                           c4ac41ec-00f2-45e1-9add-7cad6c8c249f
  GENERAL.DEVICES:                        ens33.100
  GENERAL.IP-IFACE:                       ens33.100
  GENERAL.STATE:                          activated
  GENERAL.DEFAULT:                        yes
  GENERAL.DEFAULT6:                       no
  GENERAL.SPEC-OBJECT:                    --
  GENERAL.VPN:                            no
  GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/ActiveConnection/419
  GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/Settings/3
  GENERAL.ZONE:                           --
  GENERAL.MASTER-PATH:                    --
  IP4.ADDRESS[1]:                         192.168.56.11/24
  IP4.GATEWAY:                            192.168.56.1
  IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.56.1, mt = 400
  IP4.ROUTE[2]:                           dst = 192.168.56.0/24, nh = 0.0.0.0, mt = 400
  IP6.ADDRESS[1]:                         fe80::72a:1413:609c:8f78/64
  IP6.GATEWAY:                            --
  IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 1024
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
